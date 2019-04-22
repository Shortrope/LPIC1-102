# Security

## `who`, `w`
List currently logged in users

## `last`
List of everyone who has logged in (currently logged out)  
Find failed login attempts:

    last -f /var/log/btmp

## `lsof`
List open files  
Open ports are considered files, so will show here as well  

    lsof -u mario           # open files for a user
    lsof /root              # open files in a directory

## `find`
Find files with 'setuid'

    find / perm -u+s
    find / perm 04000

Find files with 'setgid'

    find / perm -g+s
    find / perm 04000

## `ulimit`
Set limits on amount of resources that a user can utilize  

    ulimit -a
    ulimit -m 2048          # limit to 2G of ram per user

Add the following line to make memeory limit permanent for user mario to /etc/security/limits.conf  

    mario   hard    memlock     2048

Limit logins for a group

    @engineering    -   maxlogins   2       # @ = group, - = hard and soft

Cpu time per process for a user

    mario   soft    cpu     150
    mario   hard    cpu     200

## `change`
Password expiration info  
Also see the passwd and shadow files for pw info

## Elevated Privileges

### /etc/sudoers
Config file for users or groups with privileges  
Use `visudo` to edit the file

    root    ALL=(ALL)   ALL
    %wheel  ALL=(ALL)   ALL
    %wheel  ALL=(ALL)   NOPASSWD: ALL

    groups mario

Limit command a sudo user can run

    ??

### su
Switch user

    su - mario          # - = use the users shell environment