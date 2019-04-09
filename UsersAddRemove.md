# Add Remove Users

## `useradd`
    useradd -m -G devs -c "Jay Smith CNE" -s /bin/zsh jsmith
        -m  create home directory
        -G  supplementary group
        -c  Comment
        -s  shell

## `passwd`
    passwd                  # change password for current user
    passwd jsmith
    passwd -e jsmith        # expire.. user must set a new pw at next login

## `userdel`
    userdel jsmith          # does not remove home directory
    userdel -r jsmith       # remove home dir


## add existing user to a group
    usermod -aG devs jsmith