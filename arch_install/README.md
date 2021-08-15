Это гайд по установке Arch Linux для моих нужд с моими настройками и удобствами.

1. Настроить Wi-Fi wifi.md  
2. Включить синхронизацию времени  
```
    timedatectl set-ntp true
    timedatectl set-timezone Europe/Moscow
```
3. Разбить диск (он уже разбит)  
```
    cfdisk /dev/sda
    # только создание разделов, далее форматирование
    mkfs.fat -F32 /dev/sda1
    mkfs.ext4 /dev/sda2
    mkfs.ext4 /dev/sda3
```
4. Сформатировать диски  
```
    mkfs.ext4 /dev/root_partition
    mkswap /dev/swap_partition
```
5. Смонтировать диски  
```
    mount /dev/root_partition /mnt
    mkdir -p /mnt/boot/efi
    mount /dev/efi_partition /mnt/boot/efi
    swapon /dev/swap_partition
```
6. Установить необходимые пакеты  
```
    pacstrap /mnt base base-devel linux linux-firmware linux-headers iproute2 dhcpcd sudo nano vim man man-db man-pages texinfo iwd grub efibootmgr amd-ucode os-prober zsh ntfs-3g exfat-utils iw wpa_supplicant 
```
7. Сгенерировать fstab  
```
    genfstab -U /mnt >> /mnt/etc/fstab
```
Проверить наличие swap  
8. Заходим в систему  
```
    arch-chroot /mnt
```
9. Настраиваем время  
```
    ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime
    hwclock --systohc
```
10. Настраиваем язык  
Открываем `en_US.UTF-8` и `ru_RU.UTF-8` в `/etc/locale.gen`  
Создаем `/etc/locale.conf` с контентом `LANG=en_US.UTF-8`
```    
    locale-gen
```  
11. Назвать себя в интернете `/etc/hostname` : `alex-rog14`  
12. Добавить сопоставления `/etc/hosts`  
```
    127.0.0.1        localhost
    ::1              localhost
```	 
13. Делаем пароль рута  
```
    passwd
```  
14. Устанавливаем старый добрый grub  
```
    grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB
    grub-mkconfig -o /boot/grub/grub.cfg
``` 
Если не видит винду, добавить в `/etc/default/grub`
```
    GRUB_DISABLE_OS_PROBER=false
```
15. Ребутаемся

.....
1. Создаем пользователя
```
    useradd -m -g users -G wheel -s /usr/bin/zsh alex
    passwd alex
    EDITOR=vim visudo
```
Расскоментировать `%wheel ALL=(ALL) ALL`  
2. Добавляем `[multilib]`, раскомментировав его в `/etc/pacman.conf`  
```
    pacman -Sy
```
3. Устанавливаем xorg
```
    sudo pacman -S xorg xorg-xinit xorg-server
```
4. Выходим из root
```
    exit
```
5. Устанавливаем KDE 
```
    pacman -S plasma-meta packagekit
    systemctl enable NetworkManager
    systemctl enable sddm
``` 
Шрифты предпочитаю `noto`, `proton-gstreamer`  
6. Устанавливаем консоль
```
    pacman -S konsole
```
Ребутаемся  

7. Настраиваем pipewire
```
    sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack
```
8. Настраиваем bluetooth
```
    sudo pacman -S bluez bluez-utils
    systemctl enable bluetooth
    systemctl start bluetooth
```
9. Устанавливаем yay
```
    git clone https://aur.archlinux.org/yay.git
    cd yay
    makepkg -si
```
10. Устанавливаем доп пакеты
```
    yay -Sy wget \ # позволяет выполнять HTTP-запросы, скачивать файлы
      curl \ # делает то же самое, что и предыдущий
      ttf-droid \ # шрифт по-умолчанию для VScode
      firefox \ # firefox
      gparted \ # графическая оболочка для разметки дисков
      htop \ # показывает запущенные процессы, загрузку cpu и потребление памяти
      smartmontools \ # утилита для проверки состояния SSD
      telegram-desktop \ # лучший мессенджер
      texmaker \ # редактор LaTex, генерирует PDF
      qbittorrent \ # торрент клиент
      smplayer \ # видео плеер
      jq \ # Утилита для работы с JSON
      httpie \ # лучшая замена curl с подсветкой вывода
      code \ # visual studio code
      yandex-browser-beta \ # Yandex browser
      libreoffice-still \ # Офис
      dolphin \ # Файловый менеджер
      ark \ # Менеджер архивов
    a2jmidid \
    alsa-plugins \
    alsa-utils \
    amd-ucode \
    amdvlk \
    amsynth \
    android-tools \
    ark \
    asusctl-git \
    autoconf \
    automake \
    base \
    binutils \
    bison \
    blender \
    bluez-utils \
    boost \
    cli11 \
    cmake \
    code \
    dhcpcd \
    discord \
    dolphin \
    easyeffects \
    efibootmgr \
    exfat-utils \
    fakeroot \
    file \
    findutils \
    firefox \
    flex \
    fluidplug-git \
    freepats-general-midi \
    gawk \
    gcc \
    gettext \
    git \
    glm \
    glxinfo \
    gparted \
    grep \
    groff \
    grub \
    gwenview \
    gzip \
    hibernator \
    htop \
    httpie \
    hunspell-en_us \
    hunspell-ru \
    hyphen-en \
    hyphen-ru \
    inetutils \
    iproute2 \
    iw \
    iwd \
    jack2 \
    jack2-dbus \
    java8-openjfx \
    jdk11-openjdk \
    jdk8-openjdk \
    jq \
    jre8-openjdk \
    jre8-openjdk-headless \
    kcalc \
    kdeconnect \
    kdenlive \
    konsole \
    laptop-mode-tools \
    lib32-amdvlk \
    lib32-libva-mesa-driver \
    lib32-mesa \
    lib32-mesa-vdpau \
    libffado \
    liblo \
    libmythes \
    libreoffice-still \
    libreoffice-still-ru \
    libtool \
    libudev0-shim \
    libva-mesa-driver \
    linux \
    linux-firmware \
    linux-headers \
    m4 \
    make \
    man-db \
    man-pages \
    mesa \
    mesa-vdpau \
    microsoft-gsl \
    mplayer \
    mythes-en \
    mythes-ru \
    nano \
    noto-fonts-emoji \
    ntfs-3g \
    nvidia \
    nvidia-prime \
    nvidia-settings \
    okular \
    opencl-amd \
    openvpn \
    os-prober \
    packagekit \
    pacman \
    pacman-contrib \
    patch \
    pipewire-alsa \
    pipewire-docs \
    pipewire-jack \
    pipewire-pulse \
    pkgconf \
    plasma-meta \
    python-pip \
    qbittorrent \
    qjackctl \
    qsynth \
    rar \
    realtime-privileges \
    ruby-fusuma \
    ruby-fusuma-plugin-sendkey \
    samba \
    sdbus-cpp \
    sed \
    smplayer \
    soundfont-fluid \
    spectacle \
    sudo \
    telegram-desktop \
    texinfo \
    texmaker \
    ttf-droid \
    update-grub \
    vim \
    vlc \
    vulkan-tools \
    wget \
    which \
    wine \
    wpa_supplicant \
    xdotool \
    xf86-video-amdgpu \
    xorg-bdftopcf \
    xorg-docs \
    xorg-font-util \
    xorg-fonts-100dpi \
    xorg-fonts-75dpi \
    xorg-fonts-encodings \
    xorg-iceauth \
    xorg-mkfontscale \
    xorg-server \
    xorg-server-common \
    xorg-server-devel \
    xorg-server-xephyr \
    xorg-server-xnest \
    xorg-server-xvfb \
    xorg-sessreg \
    xorg-setxkbmap \
    xorg-smproxy \
    xorg-twm \
    xorg-x11perf \
    xorg-xauth \
    xorg-xbacklight \
    xorg-xclock \
    xorg-xcmsdb \
    xorg-xcursorgen \
    xorg-xdpyinfo \
    xorg-xdriinfo \
    xorg-xev \
    xorg-xgamma \
    xorg-xhost \
    xorg-xinit \
    xorg-xinput \
    xorg-xkbcomp \
    xorg-xkbevd \
    xorg-xkbutils \
    xorg-xkill \
    xorg-xlsatoms \
    xorg-xlsclients \
    xorg-xmodmap \
    xorg-xpr \
    xorg-xprop \
    xorg-xrandr \
    xorg-xrdb \
    xorg-xrefresh \
    xorg-xset \
    xorg-xsetroot \
    xorg-xvinfo \
    xorg-xwayland \
    xorg-xwd \
    xorg-xwininfo \
    xorg-xwud \
    xterm \
    yandex-browser-beta \
    yay \
    zephyrusbling-git \
    zita-ajbridge \
    zoom \
    zsh \

```
TODO: Настройка темы grub, ssh и fusuma
