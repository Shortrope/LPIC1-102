# User and Group Modifications

## `usermod`
    usermod -s /bin/zsh mario
    getent passwd mario
    groupadd devs
    usermod -aG devs mario          # -a  append,  -G  group
    getent group devs

## Lock account

    usermod -L mario
    getent shadow mario     # ! at beginning of encrypted pw
    usermod -U mario        # unlock

## Change shell

    useradd -r projectx                     # -r to create a 'system' user
    usermod -s /sbin/nologin projectx
    usermod -d /opt/projectx projectx       # change home dir.. must create the dir and chg ownership

## `chage` : Change password age
List and modigy aging parameters of a user's pw

    chage -E 2019-05-30 mario       # -E  expire date
    chage -l mario                  # -l  list account options
    chage -E -1 mario               # -E -1  never expires
    chage -W 14 mario               # -W  warning period to change pw

## `groupmod`
    groupmod -g 1100 devs           # -g  change group id
    getent group dev

    groupmod -n Develpers devs      # -n  change group name
    getent group Developers

