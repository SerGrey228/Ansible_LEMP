# Ansible_LEMP
## Структура проекта Ansible_LEMP:
- LEMP
- ansible.conf
- defaults
- hosts
- playbook.yml

1. LEMP - роль для создания стека ПО для запуска web-сервера на linux. 
2. ansible.conf - содержит в себе настройки для запуска ansible, а также путь к inventory-файлу
3. defaults - документ для конфигурации php-сервера
4. hosts - содержит информацию о серверах (name, group, ip, port, путь к ssh-файлу)
5. playbook.yml - файл для запуска роли LEMP

## Структура LEMP файла:
- tasks
  - default_settings.yml - playbook для обновления серверов
  - lemp_stack.yml - playbook для установки и настройки LEMP стека
  - main.yml - определяет порядок запуска playbook-ов
- vars
  - main.yml - содержит переменные для tasks
 
## Инструкция:
Уставнока LEMP производится на сервер linux debian 12, для установки требуется ssh соединение и права root для пользователя в папке sudoers на сервере

1. Установить shh соединение с сервером, для этого на устройствах выполнить команды:
   
   sudo apt install ssh, 
   sudo ssh-keygen

   Перенести ключ из /home/user/.ssh/id_rsa.pub в файл /home/user/.ssh/authtorized_keys на сервере
2. Изменить ip адрес для сервера в папке hosts (ansible_host)
3. Выполнить команду из директории ansible:

   ansible-playbook playbook.yml

4. Для просмотра php info, в браузере, в сроке поиска, ввести {ip_адресс_сервера}/test.php
