# check_daggre

> TODO: Add desciption

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Perl                            |
| Source          | Atomia custom                   |
| Original author | thorsten.tarrach@atomia.com     |

---
## Requirements
None

## Usage
### Parameters
```
check_daggre.pl 
    --uri <uri>
    --timeout <timeout>
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

<!-- ## Setup -->

## Examples

```
check_daggre.pl
    --uri http://123.123.123.123/g?a={auth}&o={instance-id}&latest=cpu_usage_ms
    --timeout 5
```