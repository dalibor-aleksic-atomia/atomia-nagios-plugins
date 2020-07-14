# check_domainreg

This script check if DomainReg service is running correctly using domainreg_client cli utility.

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Bash                            |
| Source          | Atomia custom                   |
| Original author | Unknown                         |

---

## Requirements

- domainreg_client CLI

## Usage

### Parameters
```
domainreg.sh
    <url> 
    <user>
    <pass>
    <domain> <[domain ...]>
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

<!-- ## Setup -->

<!-- ## Examples
> TODO: Add examples -->