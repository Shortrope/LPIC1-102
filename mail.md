# Mail Transfer Agent (MTA)

- MTA: routes email to its intended destination
- MDA: message delivery agent
- MUA: message user agent - email client

Common MTA Systems

- sendmail: 
    - on of the oldest MTA system
    - default on many Linux distros
    - notoriously difficult to configure
- postfix:
    - modern MTA 
    - on many linux distros
    - simpler ot configure
    - good security
= exim:
    - used to be default on debian
    - good security
    - simpler ot configure
- Sendmail Emulation Layer:
    - can use sendmail style commands on other MTAs
    

## Email Forwarding
    yum install mailx

### /etc/aliases
Config file to set up forwarding addresses for users on a system  

Format:

    user:   useraccout that will receive the mail
    bin:    root
    adm:    root
    root:   mario

### `newaliases` command
After editing /etc/aliases, run the `newaliases` cmd which will regenerate /etc/aliases.db

### /etc/aliases.db
MTA uses this db file for mail delivery  
- enter the message number to view it
- d - to delete message
- q - quit

### `mail`, `mailq` command
This will query the mail spooler for mail  

    mailq
    sendmail -bp        # same as mailq
Send a mail message

    mail -s "testing" root@localhost
    Hey Buddy
    ctrl-D

### /var/log/maillog

### ~/.forwarding
A user can setup his own forwarding rules  

    mario@sr.com

