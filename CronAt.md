# Automate Tasks, Scheduling Jobs

## `Cron`

    *  *  *  *  *  user-name  cmd

    minute          0 - 59
    hour            0 - 23
    day of month    1 - 31
    month           1 - 12
    day of week     0 - 6  Sunday = 0

    */3 * * * * cmd     # every 3 mins


    crontab -e      # edit
    crontab -l      # list
    crontab -r      # remove 
    crontab -r -u mario     # remove user mario's crontab
    crontab -l -u mario     # list user mario's crontab

### System crontab files
Just drop scripts into these directories

    /etc/cron.hourly/
    /etc/cron.daily/
    /etc/cron.weekly/
    /etc/cron.monthly/

/etc/cron.d/  add files in the crontab format

    /etc/cron.d/raid-check

/etc/cron.deny:  list of user names not allowed to use cron

## `at`
Schedule a one time job

    yum install at
    systemctl start atd.service
    systemctl enable atd.service

### Run commands at a specific time

    at now + 5 minutes
    at 4:00 AM tomorrow
    at> cmd 1
    at> cmd 2
    at> ctrl-D

### Run a script

    at -f /root/program.sh 10:15 PM Oct 8

    atq             # view job queue
    atrm 3          # remove a scheduled job by job number
    /etc/at.allow   # user list allowed to schedule 'at' jobs
    /etc/at.deny    # user list denied to schedule 'at' jobs

## Systemd Timer Units ???
Timer controlled by systemd  
Each `.timer` file will have a matching `.service` unit file  

man 5 systemd.timer  
man 7 systemd.time

    systemctl list-timers --all
    systemctl cat systemd-tmpfiles-clean.timer
    systemctl cat systemd-tmpfiles-clean.service
    systemctl enable systemd-tmpfiles-clean.timer
    systemctl start systemd-tmpfiles-clean.timer

Transient

    systemd-run --on-active=