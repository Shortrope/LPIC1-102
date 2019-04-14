# System Time Locale Internatioalization

## `locale`
Displays locale info

    locale

### `localectl`
Set the default system language and character encoding

    localectl
    localectl list-locales      # list all availabel locale

Set the LANG env variable

    LANG=pl_PL.utf8                         # polish
    localectl set-locale el_GR.iso88597

error messages... will be in polish  
man pages still in english. Need to install polish man pages

    yum install man-pages-pl

### Character encoding

    utf8
    iso8859xx                   # has 15 parts

### What encoding does a file use
    file -i file1.txt

### `iconv`: convert encoding
    iconv -f ISO-8859-1 -t UTF-8 -o newfile.txt file1.txt   # -f  from
                                                            # -t  to
                                                            # -o output to file

## Time and Date

    date
    date -u                         # UTC format
    date +%F                        # +   format modifier
    date +%m/%d/%Y                  # 04/13/2019

    date -s "01/01/2019 12:00:00"   # -s  set time on system untile next boot

### `timedatectl`
Display date time settings  
Update system time and RTC clock  

    timedatectl set-time "01/01/2019 12:00:00"          # set time permanently

### Timezone

    timedatectl list-timezones
    timedatectl set-timezone "Antarctica/Davis"

#### `tzselect`
Menu driven cmd to help set timezone  
It only gives you the text to set the timezone in a profile or script

    tzselect

### Timezone files

    /etc/localtime
    /etc/timezone
    /usr/share/zoneinfo

## NTP
Stratum 0:  Very precise clocks  
Stratum 1:  Sync with each other and get time from stratum 0  
Stratum 2:  All other devices get time from here  

### `ntpd`
Service that checks upstream time servers for correct time  
Uses UTP 123  

### `ntpdate
Force system to check and update its time  
ntpd should not be running  

    ntpdate 1.pool.ntp.org

### `/etc/ntp.conf
ntpdate does not use this file
ntpd does use this file  

    server 0.pool.ntp.org iburst
    server 1.pool.ntp.org iburst
    server 2.pool.ntp.org iburst
    server 3.pool.ntp.org iburst

### `ntpq`
Query the ntpd daemon for info

    ntpq -pn        # -p  print time servers
                    # -n  number: show IP addresses

### `chronyd`
Modern NTP daemon for systemd

    /etc/chrony/chrony.conf
    systmectl start chronyd.service
    chronyc             # query chrony daemon for info
        activity        # get info
        sources         # get sources

## other commands

    timedatectl 
    timedatectl set-ntp on
