linuxmint
=========

## wicd

Stop network manager:

    sudo stop network-manager
    
Create an override file for the upstart job:

    sudo echo "manual" | sudo tee /etc/init/network-manager.override
    
Disable Network in Startup Application Preferences

## speed up

    sudo pluma /etc/sysctl.conf
Edit:
> vm.swappiness=<strong>10</strong>


    sudo pluma /etc/initramfs-tools/conf.d/resume
Edit:
> **\#RESUME**=UUID=


    sudo pluma /etc/default/grub
Edit:
> GRUB_TIMEOUT=<strong>0</strong>  
> GRUB_FORCE_HIDDEN_MENU=<strong>"true"</strong> 
> **export GRUB_FORCE_HIDDEN_MENU**


    sudo pluma /etc/grub.d/30_os-prober
Add:
> "if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then  
>   
>   
> &nbsp;&nbsp;cat <<EOF  
> &nbsp;&nbsp;if [ "x\${timeout}" != "x-1" ]; then  
> &nbsp;&nbsp;&nbsp;&nbsp;if keystatus; then  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if keystatus --shift; then  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;set timeout=-1  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;set timeout=0  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fi  
> &nbsp;&nbsp;&nbsp;&nbsp;else  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if sleep$verbose --interruptible 3 ; then  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;set timeout=0  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fi  
> &nbsp;&nbsp;&nbsp;&nbsp;fi  
> &nbsp;&nbsp;fi  
> &nbsp;&nbsp;EOF"


    sudo update-grub

&nbsp;

    sudo pluma /etc/fstab
Move /tmp to RAM:
> tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

Startup Applications

## useful packages

> skype-bin, ttf-mscorefonts-installer, compizconfig-settings-manager, zram-config, preload, ibus-unikey, texmaker, texlive-lang-vietnamese, calibre

## dockbarx, variety

    sudo add-apt-repository ppa:dockbar-main/ppa
    sudo add-apt-repository ppa:peterlevi/ppa
    sudo apt-get update
    sudo apt-get install dockbarx-mate variety

## thunderbird

edit->preferences->advanced->config editor->network.protocol-handler.warn-external.http;true

edit->preferences->advanced->config editor->network.protocol-handler.warn-external.https;true

edit->account settings->composition->start my reply above the quote

add-ons FireTray

Add Thunderbird to startup

## compiz

Open mateconf-editor

Change **/desktop/mate/session/required_components/windowmanager** to **compiz**

Desktop Cube->Skydom->/home/fehiepsi/Pictures/Skydome/Happy.jpg, Rotate Cube, Animations->Minimize->Magic Lamp, Ring Switcher, Place Windows, Move Windows, Resize Window, Wobbly Windows, Window Decoration

## set fully transparent panel

    sudo cp -R /usr/share/themes/Mint-X ~/.themes/
    sudo pluma ~/.themes/Mint-X/gtk-2.0/Apps/panel.rc
Edit:
> <strong>\#</strong>"Panel/panelbg.png"

Go to Menu > Applications > Preferences > Appearance, switch to the other theme and then back to the Mint-X theme.

## chrome

Set zoom 110%
