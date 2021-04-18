1. Установить nvidia драйвер  
```
    sudo pacman -S nvidia
```
Ребутнуться  
2. Установить amdgpu
```
    sudo pacman -S mesa lib32-mesa xf86-video-amdgpu amdvlk lib32-amdvlk libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau
    vim /
```
Написать 
```
Section "Device"
     Identifier "AMD"
     Driver "amdgpu"
     Option "VariableRefresh" "true"
EndSection
```
4. Установить asus-nb-ctrl-git  
```
    yay -S asus-nb-ctrl-git
    systemctl daemon-reload && systemctl restart asusd
```
3. Настроить его
```
    systemctl --user enable asus-notify.service
    systemctl --user start asus-notify.service
```
4. Забиндить Fn+F5 на `asusctl profile -n`
