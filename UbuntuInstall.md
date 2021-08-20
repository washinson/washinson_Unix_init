# Ubuntu
```
sudo apt update
sudo apt full-upgrade
reboot
```

```
sudo apt install kde-plasma-desktop 
-- select sddm --
reboot
```

```
sudo apt install sddm-theme-breeze
-- install sddm theme --
```

```
sudo apt install wget curl firefox gparted htop smartmontools telegram-desktop texmaker qbittorrent smplayer jq httpie libreoffice dolphin ark android-tools-adb android-tools-fastboot cmake gcc gettext git grep gzip iproute2 iw openjdk-11-jdk openjdk-8-jdk kcalc konsole make nano okular openvpn python3 python3-pip rar kde-spectacle sudo vim vlc wine wpasupplicant xdotool libinput-tools ruby zsh kate
```

```
reboot
```   

```
sudo gem install fusuma
mkdir ~/.config/fusuma
```
Copy to ~/.config/fusuma/config.yml
```
swipe:
  3:
    left:
      #workspace: 'next'
      #command: 'xdotool key super+period' # History forward
      sendkey: "LEFTMETA+dot"
    right:
      #workspace: 'prev'
      #command: 'xdotool key super+comma' # History back
      sendkey: "LEFTMETA+comma"
    up:
      command: 'xdotool key control+F9'
    down:
      command: 'xdotool key control+F9'

rotate:
  3:
    clockwise:
      command: 'xdotool key XF86MonBrightnessUp' # Brightness up
    counterclockwise:
      command: 'xdotool key XF86MonBrightnessDown' # Brightness down
```

Setting shortcuts
```
wget https://raw.githubusercontent.com/washinson/washinson_Unix_init/main/scheme.kksrc -O scheme.kksrc
```
And import it

setting zsh https://github.com/washinson/washinson_Unix_init/blob/main/setting_zsh.sh
```
wget https://raw.githubusercontent.com/washinson/washinson_Unix_init/main/setting_zsh.sh -O setting_zsh.sh
./setting_zsh.sh && rm setting_zsh.sh
```


Manually install
```
code, idea, yandex-browser-beta, zoom
```
