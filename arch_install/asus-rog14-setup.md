1. Установить nvidia драйвер  
```
    sudo pacman -S nvidia nvidia-prime nvidia-settings
```
2. Установить amdgpu
```
    sudo pacman -S mesa lib32-mesa xf86-video-amdgpu amdvlk lib32-amdvlk libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau
```
3. Скорее всего удалить open source драйвер
```
    pacman -Rdd xf86-video-nouveau xf86-video-amdgpu
```
Ребутнуться  

4. Установить asus-nb-ctrl-git  
```
    yay -S asus-nb-ctrl-git
    systemctl daemon-reload && systemctl restart asusd
```
5. Настроить его
```
    systemctl --user enable asus-notify.service
    systemctl --user start asus-notify.service
```
6. Забиндить Fn+F5 на `asusctl profile -n`
