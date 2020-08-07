# otus
Otus studes project
в начале были установлены все программы необходимые для выполнения домашнего задания:
1) ОС Ububntu 20.04
2) sudo apt install virtualbox
3) sudo apt install vagrant
4) sudo apt install packer
Было произведено клонирование и запуск обновления ядра
git clone git@github.com:<user_name>/manual_kernel_update.git
из папки manual_kernel_update поднят вагрант и, в соответствии с методичкой, обновлено ядро centos c 3-го до5-го
после єтого, с помощью packer создал свое ядро. здесь пришлось повозиться, т.к. репозитория, который был указан в методичке не было и пришлось искать новый и, 
соответственно править строки в centos.json:
"artifact_description": "CentOS 7.7 with kernel 5.x",
    "artifact_version": "7.7.1908",
    исправил на:
    "artifact_description": "CentOS 7.8 with kernel 5.x",
    "artifact_version": "7.8.2003",
 
 "iso_url": "http://mirror.yandex.ru/centos/7.7.1908/isos/x86_64/CentOS-7-x86_64-Minimal-1908.iso",
    "iso_checksum": "9a2c47d97b9975452f7d582264e9fc16d108ed8252ac6816239a3b58cef5c53d",
    "iso_checksum_type": "sha256",
    исправил на:
     "iso_url": "http://mirror.yandex.ru/centos/7.8.2003/isos/x86_64/CentOS-7-x86_64-Minimal-1908.iso",
    "iso_checksum": "659691c28a0e672558b003d223f83938f254b39875ee7559d1a4a14c79173193",
    "iso_checksum_type": "sha256",
после этого, командой packer build centos.json пересобрал свой образ системы
командой vagrant box add --name centos-7-5 centos-7.8.2003-kernel-5-x86_64-Minimal.box добавил в вагрант пересобранный образ
создал новую папку и в ней инициировал vagrantfile и там уже поднял vagrant up
Дальше по описанию пункта Vagrant cloud из методички. не удалось только автоматически выгрузить туда образ системы ( пришлось это делать в ручную), т.к. были проблемы с ssl-connectom, 
не смог их побороть.
Все получилось, спасибо Гуглу)
