# Arch Linux packages Cheat Sheet AntenehDev

## Try to install all <span style="color:Green"> *__pacman__*</span> packages as <span style="color:Green"> **_root_**</span> so you won't type sudo & your passcode every time you have to install package  

## <span style="color:Red">**NEVER** </span> install <span style="color:Red"> **AUR**</span> packages as <span style="color:Red">*root*</span> or <span style="color:Red">*sudo* </span>


>update & upgrade packages
```bash
pacman -Suyy
```
---

> Replace dmenu with rofi
```bash
pacman -S rofi
#goto /home/anteneh/.i3/config & add 
bindsym $mod+d exec rofi -show run -lines 4 -eh 2 -width 100 -padding 300
#comment 
#bindsym $mod+d exec dmenu
#goto /home/anteneh/.Xresources & add
rofi.color-enabled: true
rofi.color-window: #A6222227
rofi.color-normal: #273238, #c1c1c1, #273238, #394249, #ffffff
rofi.color-active: #273238, #80cbc4, #273238, #394249, #80cbc4
rofi.color-urgent: #273238, #ff1844, #273238, #394249, #ff1844
```
---
>URXVT transparent 
```bash
#goto /home/anteneh/.Xresources & add
URxvt.background:                 [80]#000000
```
---

>Dolphin
```bash
pacman -S dolphin
#select no. 1
```
---

>pip
```bash
pacman -S python-pip
```
---

>sound driver
```bash
pacman -S pulseaudio pulseaudio-alsa pulseaudio-bluetooth pulseaudio-equalizer pulseaudio-jack pulseaudio-lirc pulseaudio-zeroconf
```
---

>Microcode
```bash
#for intel processors with grub bootloader
pacman -S intel-ucode
grub-mkconfig -o /boot/grub/grub.cfg
#for AMD processors install linux-firmware package
pacman -S linux-firmware
```
---

>Disable GRUB delay NOTE only if YOUDONT DUAL BOOT
```bash
#add the following lines to the file /etc/default/grub to achieve the fastest possible boot
sudo vim /etc/default/grub
#add this line & save & exit
GRUB_FORCE_HIDDEN_MENU="true"
#create a file called 31_hold_shift copy & past the text from the link into to 31_hold_shift & then move 31_hold_shift to /etc/grub.d/
[31_hold_shift](https://gist.githubusercontent.com/anonymous/8eb2019db2e278ba99be/raw/257f15100fd46aeeb8e33a7629b209d0a14b9975/gistfile1.sh "31_hold_shift")
vim 31_hold_shift
sudo mv 31_hold_shift /etc/grub.d/
#make it executable, and regenerate the grub configuration & reboot to see the changes
sudo chmod a+x /etc/grub.d/31_hold_shift
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo reboot
#so to see grub menu you need to hold shift during the startup
```
---

>QEMU/KVM
```bash
pacman -S qemu virt-manager
systemctl enable libvirtd.service
systemctl start libvirtd.service
```
---

>vscode
```bash
yaourt -S visual-studio-code-bin --noconfirm
```
---

>Qbittorrent
```bash
pacman -S qbittorrent
```
---

>Audacity
```bash
pacman -S audacity
```
---

>Deadbeef
```bash
pacman -S deadbeef
```
---

>SimpleScreenRecroder
```bash
pacman -S simplescreenrecorder
```
---

>OBS Studio
```bash
pacman -S obs-studio
```
---

>Cheese
```bash
pacman -S cheese
```
---

>Spotify & Blockify
```bash
yaourt -S spotify --noconfirm
yaourt -S blockify --noconfirm
```
---

>Java JDK
```bash
yaourt -S jdk --noconfirm
sudo archlinux-java set java-11-jdk
yaourt -S jre --noconfirm
sudo archlinux-java set java-10-jre/jre
sudo archlinux-java set java-11-jdk
archlinux-java status
java --version
```
---

>ADB
```bash
pacman -S android-tools android-udev
```
---

>Google chrome
```bash
yaourt -S google-chrome --noconfirm
```
---

>ungoogled-chromium
```bash
yaourt -S ungoogled-chromium --noconfirm
```
---
 
>YouTube-dl
```bash
pacman -S youtube-dl
```
---

>UMLET (like viso)
```bash
yaourt -S umlet --noconfirm
```
---

>Pycharm Community Edition
```bash
pacman -S pycharm-community-edition
```
---

>SublimeText
```bash
yaourt -S sublime-text-dev --noconfirm
```
---

>Slack
```bash
yaourt -S slack-desktop --noconfirm
```
---

>Android Studio
```bash
yaourt -S android-studio --noconfirm
```
---

>Virtualbox
```bash
uname -r 
#download virtualbox that matches your linux kernel
pacman -S virtualbox
modprobe -a vboxdrv
```
---

>Genymotion
```bash
yaourt -S genymotion --noconfirm
```
---

>Easytag
```bash
pacman -S easytag
```
---

>LMMS
```bash
pacman -S lmms
```
---


>Blender
```bash
pacman -S blender
```
---

>Inkscape
```bash
pacman -S inkscape
```
---

>Corebird
```bash
pacman -S corebird 
```
---

>FeedReader
```bash
pacman -S feedreader
```
---

>FileZilla
```bash
pacman -S filezilla
```
---

>Firefox Developer Edition
```bash
pacman -S firefox-developer-edition
```
---

>PuTTY
```bash
pacman -S putty
```
---

>Telegram Desktop
```bash
pacman -S telegram-desktop
```
---

>Zenmap
```bash
pacman -S nmap 
```
---

>Wireshark
```bash
pacman -S wireshark-qt
```
---

>Node
```bash
pacman -S nodejs
```
---

>check node version
```bash
node -v
node --version
```
---

>npm
```bash
pacman -S npm
```
---

>check npm version
```bash
npm --version
#OR
npm -v  #but most of the time it won't work
```
---

>Angular CLI
```bash
npm install -g @angular/cli
npm new app-name
#OR
ng new app-name --minimal	#if you don't want the test files
cd app-name
ng serve
#OR
ng serve --open   #the --open (or just -o) option automatically opens your browser to http://localhost:4200/
```
---

>Check angular version
```bash
ng --version
#OR 
ng -v	#but most of the time it won't work
```
---

>Ionic & Cordova
```bash
npm install -g ionic cordova
#config ionic
cd Documents/Dev
mkdir ionic
cd ionic
ionic start testapp blank
No
n
cd testapp && ionic serve
#OR
cd ./testapp
```
---

>WPS-office
```bash
cd Downloads
git clone https://aur.archlinux.org/wps-office.git
cd wps-office
yaourt -S libpng12 --noconfirm #only if it ask for dependency
makepkg
su
ls   #copy & paste the pkg file called wps-office_10.1.0.6757-1-x86_64.pkg.tar
pacman -U wps-office_10.1.0.6757-1-x86_64.pkg.tar
```
---

>Start bluetooth if not working
```bash
systemctl start bluetooth.service
systemctl enable bluetooth.service
```
---

>DB Browser for sqlite
```bash
pacman -S sqlitebrowser
```
---

>PostgreSQL
```bash
pacman -S postgresql
```
---

>Cisco packet tracer
```bash
yaourt -S packettracer61 --noconfirm
```
---

>Pavucontrol to control sound b/n laptop & TV(through HDMI) also other apps
```bash
pacman -S pavucontrol 
```
---

>Qutebrowser
```bash
pacman -S qutebrowser
```
---

>Remove orphans
```bash
pacman -Rns $(pacman -Qtdq)
```
---

>ffmpeg convert video
```bash
ffmpeg -i sample.mkv sampleConvert.mp4
```
---

>Dimension of your screen 
```bash
xdpyinfo | grep dimensions 
```
---

>Record screen
```bash
ffmpeg -y -f x11grab -s 1600x900 -i :0.0 recOut.mkv
```
---

>List webcam
```bash
ls /dev
#video0 is webcam 
```
---

>Record webcam
```bash
ffmpeg -y -i /dev/video0 recOut.mkv 
```
---

>Record audio & video
```bash
ffmpeg -y -f x11grab -s 1600x900 -i :0.0 -f alsa -i default recOut.mkv
```
---

>Record audio only
```bash
ffmpeg -y -f alsa -i default recOut.mkv 
```
---

>scrpy 
```bash
#install adb 
yaourt scrcpy --noconfirm
#OR
yaourt scrcpy-prebuiltserver --noconfirm 
#plug an Android device, and execute
scrcpy
#if it didn't work try using the lower resolution/bitrate with the parameters scrcpy -b2M -m800
scrcpy -b2M -m800
#if several devices are listed in adb devices, you must specify the serial
scrcpy -s 0123456789abcdef
#to show physical touches while scrcpy is running
scrcpy -t
#switch fullscreen mode
Ctrl+f
#Goto HOME screen
Ctrl+h | Middle-click
#Go BACK
Ctrl+b | Right-clickx2
#APP_SWITCH
Ctrl+s
#Goto MENU
Ctrl+m
#VOLUME_UP
Ctrl+↑ (up)
#VOLUME_DOWN 	
Ctrl+↓ (down)
#POWER 	
Ctrl+p
#turn screen on 	
Right-click²
#paste computer clipboard to device 	
Ctrl+v
#enable/disable FPS counter (on stdout) 	
Ctrl+i
#install APK from computer 	
#drag & drop APK file
```
---