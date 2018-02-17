#  The ["obsession app"](../../../obsession) launcher

A simple Ansible playbook for installing a yii2-website. Preferably with a OrangePi server on armbian.  

## What do i need?

- One clean debian-server, an [OrangePi](https://backend-university.ru) for example
- User with `ssh` and `sudo` 

Or any other debian-server and some knowledge of linux and Ansible to edit this playbook

## What will be happened?

- Ngnx, php-fpm, mysql, automysqlbackup and composer will be installed if not exists
- `/etc/nginx/sites-enabled/obsession.conf` file and `/var/www/obsession` dir will be created
- Database `account` and user `obsession` will be created in Mysql
- Also disallows a remote access for `root` in Mysql  

So **you must be sure** this changes (and maybe some else) wouldn't cause any damage on your server.
If it's clean OrangePi item - they won't.

# Installation

- Find out `ip` of your server. Let's say it's `192.168.1.100`
- Put it in `inventory.config`
- And uncomment lines in there
- Create a user with username `hacker` on your server or replace `hacker` with your own username in `inventory.config`, `webserver.yml` and `roles/mysql/vars/main.yml (also mysql_user_home)` files
- Run `ansible-playbook webserver.yml --ask-become-pass -v -i inventory.config`
- Place this line `192.168.1.100   obsession.wf` in your `/ets/hosts`
- Open `http://obsession.wf` in your browser 

If you're getting error "Failed to connect to the host via ssh: Permission denied (publickey,password).\r\n", "unreachable":
- `ssh-add ssh-copy-id <yourUsername>@<serverIp>` and try again

## Lame?

- Install it as a usual website 