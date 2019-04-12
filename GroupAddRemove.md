# Add Remove Groups

## `groups`
    groups              # displays current user group membership
    groups jsmith

## `groupadd`
    groupadd devs
    useradd -G devs -m jsmith
    usermod -aG devs jsmith

## `groupdel`
    groupdel devs