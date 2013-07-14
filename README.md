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
> vm.swappiness=10

    sudo pluma /etc/initramfs-tools/conf.d/resume
Edit:
> \#RESUME=UUID=

    sudo pluma /etc/default/grub
Edit:
> GRUB_TIMEOUT=0
> GRUB_FORCE_HIDDEN_MENU="true"
> export GRUB_FORCE_HIDDEN_MENU

    sudo pluma /etc/grub.d/30_os-prober
Add:
> if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then
>
>
>   cat <<EOF
> if [ "x\${timeout}" != "x-1" ]; then
>   if keystatus; then
>     if keystatus --shift; then
>       set timeout=-1
>     else
>       set timeout=0
>     fi
>   else
>     if sleep$verbose --interruptible 3 ; then
>       set timeout=0
>     fi
>   fi
> fi
> EOF

    sudo update-grub
    
    sudo pluma /etc/fstab
Move /tmp to RAM:
>tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

Startup Applications

## skype-bin, ttf-mscorefonts-installer, compizconfig-settings-manager, zram-config, preload, ibus-unikey, texmaker, texlive-lang-vietnamese, calibre

## dockbarx, variety
sudo add-apt-repository ppa:dockbar-main/ppa
sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update
sudo apt-get install dockbarx-mate variety

## Thunderbird
edit->preferences->advanced->config editor->network.protocol-handler.warn-external.http;true
edit->preferences->advanced->config editor->network.protocol-handler.warn-external.https;true
edit->account settings->composition->start my reply above the quote
add-ons FireTray
add Thunderbird to startup

## Compiz
mateconf-editor
/desktop/mate/session/required_components/windowmanager compiz
Desktop Cube->Skydom->/home/fehiepsi/Pictures/Skydome/Happy.jpg, Rotate Cube, Animations->Minimize->Magic Lamp, Ring Switcher, Place Windows, Move Windows, Resize Window, Wobbly Windows, Window Decoration

## Set Fully Transparent Panel
sudo cp -R /usr/share/themes/Mint-X ~/.themes/
sudo pluma ~/.themes/Mint-X/gtk-2.0/Apps/panel.rc
#"Panel/panelbg.png"
Go to Menu > Applications > Preferences > Appearance, switch to the other theme and then back to the Mint-X theme.

## Chrome
set zoom 110%
/opt/google/chrome/google-chrome --allow-outdated-plugins %U
