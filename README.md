# Install plugin

## Icinga, Nagios

Add the snippet below to /etc/icinga/objects/commands.cfg or /etc/nagios/objects/commands.cfg:

```
define command{
    command_name    check_service_restart
    command_line    $USER1$/check_service_restart
}
```

## Icinga2

```
apply Service "check_service_restart" to Host {
  import "generic-service"
  display_name = "Service restart"
  assign where "linux-servers" in host.groups
  ignore where host.name == "localhost"
  check_command = "by_ssh"
  vars.by_ssh_command = "sudo /usr/lib64/nagios/plugins/check_service_restart"
  vars.by_ssh_logname = "root"
}
```
