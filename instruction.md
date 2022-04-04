## Итак стоит задача развернуть локально GitLab на Ubuntu Server 20.04 в VMWare WorkStation.
1. В первую очередь установим необходимые зависимости (если они установлены то их установка будет пропущена).<br>
catware@gitlab-vp:~$ sudo apt-get install -y curl openssh-server ca-certificates tzdata perl<br>
2. Почтовый сервер (необходимо для отправки оповещений на почту). Если не нужны оповщенения можно скипнуть шаг<br>
catware@gitlab-vp:~$ sudo apt-get install -y postfix<br>
3. Добавим репозиторий гитлаба:<br>
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
4. Установка GitLab:<br>
catware@gitlab-vp:~$ sudo EXTERNAL_URL="http://gitlab.local" apt-get install gitlab-ce<br>
5. В hosts прописать:<br>
catware@gitlab-vp:~$ sudo nano /etc/hosts<br>
127.0.0.1 gitlab.localdomain<br>
192.168.121.34 gitlab.localdomain #статический ip адрес виртуальной машины<br>
6. Открываем в браузере 192.168.121.34, должна открыться страница авторизации:<br>
https://prnt.sc/SIjO0djhctTv<br>
7. Пароль от root посмотреть можно тут:<br>
catware@gitlab-vp:~$ sudo cat /etc/gitlab/initial_root_password<br>
## GitLab развернут!
