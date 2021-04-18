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
    swapon /dev/swap_partition
```
6. Установить необходимые пакеты  
```
    pacstrap /mnt base base-devel linux linux-firmware iproute2 dhcpcd sudo nano vim man man-db man-pages texinfo iwd grub efibootmgr amd-ucode os-prober zsh
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
    mount /dev/efi_partition /mnt/boot/efi
    grub-install --target=x86_64-efi --efi-directory=/mnt/boot/efi --bootloader-id=GRUB
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
    useradd -m -s /usr/bin/zsh alex
    passwd alex
    usermod -aG wheel alex
    visudo
```
Расскоментировать `%wheel ALL=(ALL) ALL`  
2. Добавляем `[multilib]`, раскомментировав его в `/etc/pacman.conf`  
3. Устанавливаем KDE 
```
    pacman -S plasma-meta
    systemctl enable sddm.service
``` 
Шрифты предпочитаю `noto`, `proton-vlc`  
Ребутаемся  
4. Устанавливаем софт
```
    sudo pacman -S konsole libreoffice-still
```
