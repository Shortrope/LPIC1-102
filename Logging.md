# Logging

`/var/log/dmesg`  
- kernel boot messages
- deals with hardware
- Gets recreated each time the system boots  

`var/log/messages`
- service log messages
- if a service does not have its own log file, it uses 'messages'

`var/log/secure`
- login attempts

`var/log/maillog`
- local email log - from and to this server

Logging Priority Levels  
_commit to memory_

|Value|Severity Keyword|Condition|
|:---:|:--------------:|---------|
|0    |emerg|system is unusable|
|1    |alert|action must be taken immediately|
|2    |crit|critical contition|
|3    |err|error conditions|
|4    |warn|warning conditions|
|5    |notice|normal but significant|
|6    |info|informational|
|7    |debug|debug level messages|

    dmesg --level=err,warn
    dmesg -x --level=err,warn       # -x  human readable 'facility' and 'error level'

`Facility` is the item generating a log message

|Facility|Description|
|:------:|-----------|
|kern    |Kernel messages|
|user    |Random user-level messages|
|mail    |Mail system messages|
|daemon  |System daemon messages|
|auth    |Security Authorization |
|syslog  |internal syslogd |
|lpr     |Line printer subsystem |
|news    |Network news subsystem |

## `Logger`
Send log messages to the /var/log/messages file  

    logger "hey buddy"
    logger -t "from-script" Bad input, try again.       # -t tag



## Rsyslog - Legacy logging service
`/etc/rsyslog.conf`
man rsyslog.conf

`/etc/logrotate.conf`

`/etc/logrotate.d/`

### `logrotate`

    syslogd-listfiles           # list daily log files
    syslogd-listfiles -w        # list weekly log files

    savelog                     # does the log rotate work based on /etc/syslog.conf

    /etc/logrotate.d/n
    /etc/init.d/sysklogd --quiet reload



## Systemd Journal
jouralctl

## Journalctl