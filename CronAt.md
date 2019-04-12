# Automate Tasks, Scheduling Jobs

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

## System crontab files
Just drop scripts into these directories

    /etc/cron.hourly/
    /etc/cron.daily/
    /etc/cron.weekly/
    /etc/cron.monthly/

/etc/cron.d/  add files in the crontab format

    /etc/cron.d/raid-check

/etc/cron.deny:  list of user names not allowed to use cron