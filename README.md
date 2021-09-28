# born2beroot
This project aims to introduce you to the wonderful world of virtualization. You will create your first machine in VirtualBox (or UTM if you can’t use VirtualBox) under specific instructions. Then, at the end of this project, you will be able to set up your own operating system while implementing strict rules.

Difference Between CentOS and Debian
https://www.educba.com/centos-vs-debian/

APPArmor
AppArmor - это система управления доступом к файлам на основе имен (Mandatory Access Control).
https://losst.ru/nastrojka-apparmor-v-ubuntu-16-04
	sudo aa-status

LVM
Logical volume management provides a higher-level view of the disk storage on a computer system than the traditional view of disks and partitions. This gives the system administrator much more flexibility in allocating storage to applications and users.

Storage volumes created under the control of the logical volume manager can be resized and moved around almost at will.

    PV : Physical Volumes. This means the hard disk, hard disk partitions, RAID or LUNs from a SAN which form "Physical Volumes" (or PVs).
    VG : Volume Groups. This is a collection of one or more Physical Volumes.
    LV : Logical Volumes. LVs sit inside a Volume Group and form, in effect, a virtual partition.
    PE : Physical Extents. In order to manipulate the actual data, it is divided into blocks of data called Physical Extents.
    LE : Logical Extents. Similar to Physical Extents, but at the Logical Volume level. Physical Extents are to Physical Volumes as Logical Extents are to Logical Volumes. The size of blocks are the same for each logical volume (LV) in the same volume group (VG).
https://wiki.debian.org/LVM
https://serveradmin.ru/nastrojka-diskov-v-debian/

SSH
Технология SSH или Secure Shell позволяет пользователям подключаться к компьютеру с Linux или серверу удалённо и выполнять на нём команды, так как бы они вводились с клавиатуры непосредственно на нём. Вывод команд тоже передаётся в реальном времени в текстовом режиме, от чего складывается впечатление, что вы работаете непосредственно на той машине, к которой подключены.
https://losst.ru/nastrojka-ssh-v-debian
	sudo systemctl status sshd
	vi /etc/ssh/sshd_config
	sudo systemctl restart sshd
	ssh root@localhost -p 4242
	ssh localhost -p 4242

Difference between APT and Aptitude
The first difference you will notice is that APT is a lower-level package manager, and Aptitude is a high-level package manager. This means that APT can be used in other higher-level package managers.
Another big difference is the functionality offered by both of the tools. Aptitude offers better functionality compared to apt-get. In fact, it contains the functionalities of apt-get, apt-mark, and apt-cache.
For instance, apt-get can be used effectively for package up-gradation, installation, resolving dependencies, system up-gradation, and so on. However, Aptitude offers more features thanks to the inclusion of functionalities of apt-cache and apt-mark. This means Aptitude can be used for more functionality, including package search, setting package installation as automation or manual, and more refined actions on the packages.
If you have been following closely, you by now know that Aptitude comes with an interactive UI in addition to that of the text-only. APT, on the other hand, lacks UI. This is because of the nature of apt-get as it is a low-level package manager and hence restricted to the command-line interface. As Aptitude is a high-level tool, it offers both an interactive interface along with the command-line operation.
In short, Aptitude has more features and hence can be termed as a better package management tool compared to that of apt-get.

VirtualBox
Oracle VM VirtualBox is a cross-platform virtualization application. What does that mean? For one thing, it installs on your existing Intel or AMD-based computers, whether they are running Windows, Mac OS X, Linux, or Oracle Solaris operating systems (OSes). Secondly, it extends the capabilities of your existing computer so that it can run multiple OSes, inside multiple virtual machines, at the same time. As an example, you can run Windows and Linux on your Mac, run Windows Server 2016 on your Linux server, run Linux on your Windows PC, and so on, all alongside your existing applications. You can install and run as many virtual machines as you like. The only practical limits are disk space and memory.
https://www.virtualbox.org/manual/

Check OS version
cat /etc/os-release

UFW
Брандмауэр или фаерволл — это системная утилита (сетевой экран) для контроля и фильтрации входящего/исходящего трафика. 
    - Защита системы от внешних атак. В список таких угроз входят сканирование портов, IP-спуффинг, DDoS-атаки, подбор паролей. 
    - Блокировка утечек. Если вредоносное ПО проникло в компьютер через USB или CD, то брандмауэр при соответствующих настройках предотвратит дальнейшее распространение по сети.
    - Контроль приложений. Брандмауэр позволяет настроить доступ в сеть для каждого отдельного приложения.  
    - Зональная защита. Обеспечение различных уровней доступа в рамках локальной сети. 
    - Протоколирование и предупреждение. Брандмауэр не только собирает статистику, но и предупреждает пользователей о различных действиях. 
https://losst.ru/nastrojka-ufw-ubuntu
https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-9-ru

	sudo apt install ufw
	sudo ufw enable
	sudo UFW status verbose - check status and info
	sudo ufw delete allow ssh
	sudo ufw allow ssh

	vi /etc/ufw/ufw.conf
		# Set to yes to start on boot. If setting this remotely, be sure to add a rule
		# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
		ENABLED=yes


SUDO
Утилита sudo – входит в набор программ GNU. Это небольшое приложение, выполняющее команды с привилегиями другого пользователя. Как правило, "другой" - это пользователь – root.
https://losst.ru/ustanovka-sudo-v-debian-10

Group and User

	sudo useradd sammy - создаем пользователя
	sudo groupadd Users42 - создаем группу
	sudo usermod -aG Users42 snaomi - добавляем пользователя в Группу
	getent group sudo/Users42 - смотрим список пользователей
https://losst.ru/kak-sozdat-gruppu-linux
	groupadd опции имя_группы

https://losst.ru/kak-sozdat-polzovatelya-linux
	useradd опции имя_пользователя

https://losst.ru/kak-dobavit-polzovatelya-v-gruppu-linux
	sudo usermod -a -G wheel user

Hostname
Имя компьютера или по-другому, имя хоста устанавливается во время установки системы. Оно используется для идентификации компьютера в локальной сети.
Посмотреть текущее имя компьютера можно выполнив команду hostnamectl без параметров:
	hostnamectl
https://losst.ru/kak-izmenit-imya-kompyutera-ubuntu
	sudo vi /etc/hostname

Password Policy
/etc/login.defs
/etc/pam.d/common-passwd
chage -d 0 имя_пользователя

ENV_SUPATH (string) If set, it will be used to define the PATH environment variable when the superuser login. The value is a colon separated list of paths (for example /sbin:/bin:/usr/sbin:/usr/bin) and can be preceded by PATH=. The default value is PATH=/sbin:/bin:/usr/sbin:/usr/bin.

To enforce password complexity in Debian / Ubuntu systems, you need to install  the libpam-pwquality package as shown:
	sudo apt install libpam-pwquality
pam_pwquality - PAM module to perform password quality checking 
https://linux.die.net/man/8/pam_pwquality
Let’s flesh out what these directives stand for:

    retry=3: This option will prompt the user 3 times before exiting and returning an error.
    minlen=12: This specifies that the password cannot be less than 12 characters.
    maxrepeat=3: This allows implies that only a maximum of 3 repeated characters can be included in the password.
    ucredit=-1: The option requires at least one uppercase character in the password.
    lcredit=-1: The option requires at least one lowercase character in the password.
    dcredit=-1: This implies that the password should have at last a numeric character.
    ocredit=-1: The option requires at least one special character included in the password.
    difok=3: This implies that only a  maximum of 3 character changes in the new password should be present in the old password.
    reject_username: The option rejects a password if it consists of the username either in its normal way or in reverse.
    enforce_for_root: This ensures that the password policies are adhered to even if it’s the root user configuring the passwords.

SUDO Group
https://www.tecmint.com/sudoers-configurations-for-setting-sudo-in-linux/
	sudo visudo

Shell script


Lighttpd/mariadb/php/wordpress
	https://phoenixnap.com/kb/how-to-create-mariadb-user-grant-privileges