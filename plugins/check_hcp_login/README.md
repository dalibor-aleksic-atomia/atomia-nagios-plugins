# check_hcp_login

This script checks Atomia HCP login process by mimicing user login to portal. Verification is done by checking string that can be only found on after successfull login

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Perl                            |
| Source          | Atomia custom                   |
| Original author | jimmybergman@atomia.com         |

---

## Requirements
None

## Usage
### Parameters
```
check_hcp_login.pl 
    --uri <hcp_uri>
    --user <some_username> 
    --pass '<some_pass>'
    --timeout <timeout seconds>
    --match <somestring-only-found-after-successfull-login>
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

<!-- ## Setup -->

## Examples

```sh
./check_hcp_login.pl 
    --uri https://some.uri.of.hcp/ 
    --user somelowprivuser 
    --pass 'somepass' 
    --timeout 5 
    --match somestring-only-found-after-successfull-login
```