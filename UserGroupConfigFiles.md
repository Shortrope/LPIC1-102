# User and Group Configuration Files

## /etc/passwd
    username:passwd:userid:primaryGrpID:comment:homeDir:shell

## /etc/shadow
    username:encryptedpw:dateLastChanged:minDaysChangePw:MaxDaysPwValid:PwExpirtyWarningDays:::

If ! or !! in the password field the account is locked
If * in the password field the account is locked and a password has never been set

Encrypted Password

    $6$xODlJAPQ$RWm6G1i/wSaWe.I/5h2jcghC8ketbGOsaJtSncmgw68J.hsiDAEMMcwKi6Q.nV6XyWX0o5BUKfwcPcG/NXw9E0

Encryption type | Salt | encrypted pw
- $1$ = MD5
- $5$ = SHA-256
- $6$ = SHA-512

## /etc/group

    groupname:passwd:grpid:otherUsers

passwd field  usually 'x'

## /etc/skel
Contents get copied to a new users home directory

## /etc/default/useradd

    GROUP=100
    HOME=/home
    INACTIVE=-1         # -1  acct is not disable as soon as pw expires. 0: acct is disabled
    EXPIRE=             # date acct will expire
    SHELL=/bin/bash
    SKEL=/etc/skel

## /etc/login.defs
Settings here take precedence over settings in /etc/default/useradd

## getent

    getent passwd mario
    getent group 100
