# check_atomiadns

This script check if AtomiaDNS service is running correctly by fetching SOA record using atomiadns cli utility.

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Bash                            |
| Source          | Atomia custom                   |
| Original author | Unknown                         |

---

## Requirements

- atomiadnsclient CLI

## Usage

### Parameters
```
atomiadns.sh
    <zone>
    <url>
    <user>
    <pass>
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