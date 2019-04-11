# Install and Configure X11
/etc/X11/xorg.conf
/etc/X11/xorg.conf.d/

## Wayland
- Replacement for X
- Simpler

## Installation
yum group-install "X Window Sytsem"

## Test
    systemctl get-default
        graphical.target

    cat /etc/systemd/system/default.target
        Wants=display-manager.service

    cat /etc/systemd/system/display-manager.service
        ExecStart=/usr/sbin/gdm

    echo $DISPLAY
        :0.0            # host:server.screen

    .xsession-errors    # error log

## Configuration
/etc/X11/xorg.conf
/etc/X11/xorg.conf.d/

    xdpyinfo
    X -configure

    ctrl+alt_backspc

## Remote Displays
### access to individual windows

    xhost                   # old and insecure
    xhost +

    xhost + 192.168.1.122
    ssh -Y user@192.168.1.122
    export DISPLAY="127.0.0.1:10.0"     # 10 is first remote display
    xeyes
    xauth list

### VNC
Insecure by default  

    yum -y install tigervnc-server
    



### Spice
TLS encrypted remote desktop protocol that can be used on Linux, Windows and Android  
