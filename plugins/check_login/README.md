# check_admins

This script checks login process on website by mimicing user login to website. Verification is done by checking string that can be only found on after successfull login.

> Note: This is reimplementation of `check_hcp_login` plugin

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Python                          |
| Source          | Atomia custom                   |
| Original author | dalibor.aleksic@atomia.com      |

---

## Requirements
* **BeautifulSoup4** 
  ```
  apt-get install python-bs4 python3-bs4
  ```

## Usage

### Parameters
```sh
python3 check_login.py 
    --url <login_form_url> 
    --username <username> 
    --password <password> 
    [--timeout 5] 
    [--match <matchstring>]
```
```sh
python check_login.py 
    --url <login_form_url> 
    --username <username> 
    --password <password> 
    [--timeout 5] 
    [--match <matchstring>]
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

<!-- ## Setup -->

<!-- ## Examples -->
