# Basic Shell Scripts

    $(cmd) or `cmd`
    let count=count+1

## Conditional

    if
    elif
    else
    fi

    test
    [ ]
    [[ ]]       Allows file globing, regex, ||, &&

## Loops
### `for` loop

    for i in 1 2 3 4
    do
        ... $i
    done

### `while` loop
Do something while 'true'

    count=0
    while [ $count -lt 6 ]
    do
        ...
        let count=count+1
    done

### `until` loop
Do something while 'false'

    count=10
    until [ $count -lt 1 ]
    do
        ...
        let count=count-1
    done
    

## Command substitution
Open a new shell to run the command and returns the output to the script

    $(cmd)

Run the command in the same subshell as the script

    `cmd`

Example:

    for i in $(ls /opt)
    for i in `ls /opt`

### `seq`

    for i in $(seq 1 15)        # increment by 1
    for i in $(seq 1 5 50 )     # increment by 5.  1 6 11 16...

## Other commands
### `read`
read VAR

    while read LINE
    do
        echo "$LINE"    # print each line of the file
    done < file.txt 

### `exit`

    exit 21

### `exec`
Redirect all output of this shell into a file or antother process, w/out sending it to the current shell.


    exec > out.log
    ls
    pwd
    exit
