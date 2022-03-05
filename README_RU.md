# Nemesida WAF Free - бесплатный WAF для NGINX

Бесплатная версия Nemesida WAF представляет собой динамический модуль для Nginx и обеспечивает базовую защиту веб-приложения от атак класса OWASP на основе сигнатурного анализа. Nemesida WAF Free имеет собственную базу сигнатур, выявляет атаки на веб-приложения при минимальном количестве ложных срабатываний, обновляется из Linux-репозитория, устанавливается и настраивается за несколько минут.

![Nemesida WAF Cabinet](https://nemesida-waf.com/wp-content/uploads/2019/08/1.png)

## 1. Особенности Nemesida WAF:

- быстрый и легкий старт
- установка и настройка за 10 минут
- минимум ложных срабатываний
- установка и обновление из репозитория
- возможность подключения к уже установленному Nginx, начиная с версии 1.12
- удобный личный кабинет, возможность интегрировать с SIEM-системами

## 2. Установка

Установка динамического модуля займет пару минут. Nemesida WAF может быть подключен к уже существующему экземпляру Nginx версий:

- Nginx stable, начиная с 1.12
- Nginx mainline, начиная с 1.15
- Nginx Plus, начиная с R16

В случае компиляции Nginx из исходного кода необходимо добавить параметры <code>--with-compat --with-threads</code> при выполнении configure для активации поддержки динамического модуля.

Установите Nginx (если еще не установлен) и динамический модуль Nemesida WAF:

<details>
  <summary>Debian 9</summary>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/debian/ stretch nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://nemesida-security.com/repo/nw/debian stretch non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://nemesida-security.com/repo/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install nginx python3 python3-venv python3-pip python3-dev python3-setuptools librabbitmq4 libcurl3-gnutls libcurl4-openssl-dev libc6-dev gcc rabbitmq-server libmaxminddb0 g++ memcached
# apt install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Debian 10</summary>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/debian/ buster nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://nemesida-security.com/repo/nw/debian buster non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://nemesida-security.com/repo/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install nginx python3 python3-venv python3-pip python3-dev python3-setuptools librabbitmq4 libcurl3-gnutls libcurl4-openssl-dev libc6-dev gcc rabbitmq-server libmaxminddb0 g++ memcached
# apt install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Debian 11</summary>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/debian/ bullseye nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://nemesida-security.com/repo/nw/debian bullseye non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://nemesida-security.com/repo/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install nginx python3 python3-venv python3-pip python3-dev python3-setuptools librabbitmq4 libcurl3-gnutls libcurl4-openssl-dev libc6-dev gcc rabbitmq-server libmaxminddb0 g++ memcached
# apt install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

<hr />

<details>
  <summary>Ubuntu 18.04</summary>

<pre>
# apt install apt-transport-https
</pre>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ bionic nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://nemesida-security.com/repo/nw/ubuntu bionic non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://nemesida-security.com/repo/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install nginx python3 python3-venv python3-pip python3-dev python3-setuptools librabbitmq4 libcurl3-gnutls libcurl4-openssl-dev libc6-dev gcc rabbitmq-server libmaxminddb0 g++ memcached
# apt install nwaf-dyn-1.18
</pre>

</details>

<details>
  <summary>Ubuntu 20.04</summary>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ focal nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://nemesida-security.com/repo/nw/ubuntu focal non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://nemesida-security.com/repo/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install nginx python3 python3-venv python3-pip python3-dev python3-setuptools libcurl3-gnutls librabbitmq4 libcurl4-openssl-dev libc6-dev gcc rabbitmq-server libmaxminddb0 g++ memcached
# apt install nwaf-dyn-1.18
</pre>
</details>

<hr />

<details>
  <summary>CentOS 7</summary>

Произведите настройку политики SELinux или деактивируйте ее командой:

<pre>
# setenforce 0
</pre>

после чего приведите файл <code>/etc/selinux/config</code> к виду:

<pre>
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of three two values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
</pre>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# yum update
# yum install epel-release
# rpm -Uvh https://nemesida-security.com/repo/nw/centos/nwaf-release-centos-7-1-6.noarch.rpm
# rpm -Uvh https://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
# yum install nginx python36 python36-devel python36-setuptools python36-pip openssl librabbitmq libcurl-devel rabbitmq-server gcc libmaxminddb memcached
# yum install nwaf-dyn-1.18
</pre>

</details>

<details>
  <summary>CentOS 8 Stream</summary>

Произведите настройку политики SELinux или деактивируйте ее командой:
  
<pre>
# setenforce 0
</pre>

после чего приведите файл <code>/etc/selinux/config</code> к виду:

<pre>
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of three two values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
</pre>

Произведите установку пакета:

<pre>
# dnf install dnf-utils
</pre>

Добавьте репозиторий Nginx, приведя файл <code>/etc/yum.repos.d/nginx.repo</code> к виду:

<pre>
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true
</pre>

Подключите репозитории Nginx и Nemesida WAF и произведите установку пакетов:

<pre>
# dnf update
# dnf install nginx
# dnf install python3-pip python3-devel openssl rabbitmq-server librabbitmq libcurl-devel gcc systemd
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# dnf install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

## 3. Базовая настройка

Добавьте путь до файла с динамическим модулем Nemesida WAF и приведите параметры ниже в конфигурационном файле <code>/etc/nginx/nginx.conf</code> к виду:

<pre>
load_module /etc/nginx/modules/ngx_http_waf_module.so;
...
worker_processes auto;
...
http {
...
    ##
    # Nemesida WAF
    ##

    ## Request body too large fix
    client_body_buffer_size 25M;

    include /etc/nginx/nwaf/conf/global/*.conf;
    include /etc/nginx/nwaf/conf/vhosts/*.conf;
...
}
</pre>

<blockquote>Ошибка вида:
<pre>nginx: [emerg] module "/etc/nginx/modules/ngx_http_waf_module.so" version 1017010 instead of 1018000 in /etc/nginx/nginx.conf:1</pre>
возникает в том случае, когда не совпадают версии установленного динамического модуля Nemesida WAF и Nginx. В данном случае <code>1017010</code> - версия Nginx 1.17.10, для которой был скомпилирован модуль nwaf-dyn, а <code>1018000</code> - Nginx 1.18.0, установленный на сервере. Пакет динамического модуля nwaf-dyn-1.18 предназначен для работы с Nginx версии 1.18, а nwaf-dyn-plus-r22 - для работы с <a href="https://docs.nginx.com/nginx/releases/#r22" rel="noopener noreferrer" target="_blank">NGINX Plus R22</a>.</blockquote>

Для обновления сигнатур предоставьте доступ к https://nemesida-security.com. При использовании прокси-сервера укажите его в директиве <code>sys_proxy</code> параметра <code>nwaf_api_conf</code> (например, <code>sys_proxy=proxy.example.com:3128</code>).

Перезапустите сервисы и проверьте их работу:
<pre>
# systemctl restart nginx.service nwaf_update.service
# systemctl status nginx.service nwaf_update.service
</pre>

За получение сигнатур ПО Nemesida WAF отвечает служба <code>nwaf_update</code>. Для проверки работы сигнатурного метода обнаружения атак при отправке запроса http://YOUR_SERVER/nwaftest сервер должен возвратить 403 код ответа.

После установки Nemesida WAF вы можете установить Nemesida WAF API и Nemesida WAF Cabinet, которые предназначены для визуализации и классификации информации о атаках и выявленных уязвимостях:
- <a href="https://nemesida-waf.ru/manuals/5611">Nemesida WAF API</a>
- <a href="https://nemesida-waf.ru/manuals/1446">Nemesida WAF Cabinet</a>

Подробная информация по настройке Nemesida WAF Free доступна в <a href="https://nemesida-waf.ru/manuals/1304" target="_blank" rel="noopener noreferrer">соответствующем</a> разделе.

## 4. Ссылки:

#### Документация
- Nemesida WAF: https://nemesida-waf.ru/category/manuals
- Nemesida WAF Free: https://nemesida-waf.ru/about/2511

#### Virtual Appliance & Docker images
- Docker image: https://nemesida-waf.ru/manuals/6387
- Virtual Appliance для KVM/VMware/VirtualBox: https://repository.pentestit.ru/vm/NemesidaWAF-VA.zip

#### Прочее
- Форум: https://forum.nemesida-security.com
- Набор сигнатур (автообновление): https://rlinfo.nemesida-security.com
- Демонстрационный стенд: https://demo.lk.nemesida-waf.com (demo@pentestit.ru / pentestit)
