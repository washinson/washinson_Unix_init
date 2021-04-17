Это гайд по установке Arch Linux для моих нужд с моими настройками и удобствами.

1. Настроить Wi-Fi wifi.md
2. Включить синхронизацию времени
    timedatectl set-ntp true
    timedatectl set-timezone Europe/Moscow
3. Разбить диск (он уже разбит)
4. Сформатировать диски
    mkfs.ext4 /dev/root_partition
    mkswap /dev/swap_partition
5. Смонтировать диски
    mount /dev/root_partition /mnt
    swapon /dev/swap_partition
6. Установить необходимые пакеты
    pacstrap /mnt base base-devel linux linux-firmware iproute2 dhcpcd sudo nano vim man man-db man-pages texinfo iwd
7. Сгенерировать fstab
    genfstab -U /mnt >> /mnt/etc/fstab
Проверить наличие swap
8. Заходим в систему 
    arch-chroot /mnt
9. Настраиваем время
    ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime
    hwclock --systohc
10. Настраиваем язык
Открываем `en_US.UTF-8` и `ru_RU.UTF-8` в `/etc/locale.conf`
Создаем `/etc/locale.conf` с контентом `LANG=en_US.UTF-8`
    locale-gen
11. Назвать себя в интернете `/etc/hostname` : `alex-rog14`
12. Добавить сопоставления `/etc/hosts`
    127.0.0.1        localhost
    ::1              localhost
    
13. Делаем пароль рута 
    passwd
14.  
