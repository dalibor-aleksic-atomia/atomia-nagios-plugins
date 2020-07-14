# check_admins

This script checks users on the Windows server. Users can be either local or domain based. The script will compare the list of accounts provided and if there are more users on the system than on the list the script will output CRITICAL.

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | PowerShell                      |
| Source          | Atomia custom                   |
| Original author | nikola.vitanovic@atomia.com     |

---

## Requirements
None


## Usage

### Parameters
```
check_admins.ps1
    -domain    "Domain group name"
    -local     "Local group name"
    -usernames "COMPUTER\User1,DOMAIN\User2"
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

## Setup

### Nagios client setup
Assuming you are using NSClient++ on Windows, the check script needs to be put into: `C:\Program Files\NSClient++\scripts`.

#### nsclient.ini
Configuration should be as following:
```
[/settings/NRPE/server]

...

allow arguments = true
allow nasty characters = true

[/settings/external scripts]
allow arguments = true
allow nasty characters = true

[/settings/external scripts/scripts]
check_domain_admins = cmd /c echo scripts\check_admins.ps1 -domain "Domain Admins" -usernames $ARG1$; exit($lastexitcode) | powershell.exe -command -
check_enterprise_admins = cmd /c echo scripts\check_admins.ps1 -domain "Enterprise Admins" -usernames $ARG1$; exit($lastexitcode) | powershell.exe -command -
check_local_admins = cmd /c echo scripts\check_admins.ps1 -local "Administrators" -usernames $ARG1$; exit($lastexitcode) | powershell.exe -command -
```

Here we define three most common commands for checking **Domain Admins and Enterprise Admins** domain groups and **Administrators** local group.


### Nagios server setup

Since the script is a shell script that is triggered with `check_nrpe` example call for domain admins would be:
```
/usr/local/nagios/libexec/check_nrpe -H 192.168.33.20 -t 30 -c check_domain_admins -a "ATOMIA\Administrator,ATOMIA\WindowsAdmin"
```
This would call **check_domain_admins** command in the client which then accepts parameters as on the script.

The command in Nagios would be setup like this:

Command: `$USER1$/check_nrpe -H $HOSTADDRESS$ -t 30 -c $ARG1$ -a $ARG2$`

$ARG1$: `check_domain_admins`

$ARG2$: `'"ATOMIA\Administrator","ATOMIA\WindowsAdmin"'`

or

$ARG2$: `'"ATOMIA\Administrator,ATOMIA\WindowsAdmin"'`

> **Important:** Use double quotes `'"` - wrap whole argument in `'` quotes


> **Important:** 
> Use `check_nrpe_1arg` instead `check_nrpe` as _Check command_ in Nagios UI interface.
>
> `check_nrpe_1arg` passes `$ARG2$` argument via `-a` as required, where `check_nrpe` passes `$ARG2$` via `-c` and it is not properly substituted. Powershell script will get `$` as parameter value instead value in `$ARG2$`

## Examples
Example call when all users are there, and there are no additional in group **Domain Admins**:
```
./check_admins.ps1 -domain "Domain Admins" -usernames "ATOMIA\Administrator,ATOMIA\apppooluser,ATOMIA\WindowsAdmin"
```
Returns:
```
OK - No additional users found
```
Example call when there is for example additional user that is not in the list:
Example call when all users are there, and there are no additional in group **Domain Admins**:
```
./check_admins.ps1 -domain "Domain Admins" -usernames "ATOMIA\Administrator,ATOMIA\WindowsAdmin"
```
Returns:
```
CRITICAL - 1 additional users
ATOMIA\apppooluser
```
As we can see here in the list above we did not specify the **apppooluser** which has now been shown.
