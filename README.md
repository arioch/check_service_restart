# Install plugin

## Icinga, Nagios

Add the snippet below to /etc/icinga/objects/commands.cfg or /etc/nagios/objects/commands.cfg:

```
define command{
    command_name    check_service_restart
    command_line    $USER1$/check_service_restart
}
```
