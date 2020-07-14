# check_openstack

This script check if openstack environment is up and running by provisioning temporary VM machine and removing it afterwards.

|                 |                                 |
| --------------- | ------------------------------- |
| Language        | Bash                            |
| Source          | Atomia custom                   |
| Original author | alvuk@atomia.com     |

---
## Requirements
None

## Usage

### Parameters
```
check_openstack.sh 
    <ec2_secret_key> 
    <ec2_access_key> 
    <ec2_service_url>
```

### Exit codes
```
    0 - OK
    2 - CRITICAL
    3 - UNKNOWN
```

<!-- ## Setup -->

<!-- ## Examples -->
