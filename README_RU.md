# Nemesida WAF Free - бесплатный WAF для NGINX

Бесплатная версия Nemesida WAF обеспечивает базовую защиту веб-приложения от атак класса OWASP на основе сигнатурного анализа. Nemesida WAF Free имеет <a href="https://rlinfo.nemesida-security.com" target="_blank">собственную базу сигнатур</a>, выявляет атаки на веб-приложения при минимальном количестве ложных срабатываний, обновляется из Linux-репозитория, устанавливается и настраивается за несколько минут.

![Nemesida WAF Cabinet](https://nemesida-waf.com/wp-content/uploads/2019/08/1.png)

Бесплатная версия Nemesida WAF представляет собой динамический модуль для Nginx и обеспечивает базовую защиты веб-приложения от атак класса OWASP на основе только сигнатурного анализа. Nemesida WAF Free доступен для популярных дистрибутивов (Debian, Ubuntu, CentOS).

## Особенности Nemesida WAF:

- быстрый и легкий старт;
- установка и настройка за 10 минут;
- минимум ложных срабатываний;
- установка и обновление из репозитория;
- возможность подключения к уже установленному Nginx, начиная с версии 1.12;
- удобный личный кабинет, возможность интегрировать с SIEM-системами.

## Установка

Установка динамического модуля займет пару минут. Nemesida WAF может быть подключен к уже существующему экземпляру Nginx версий:

- Nginx stable, начиная с 1.12;
- Nginx mainline, начиная с 1.17;
- Nginx Plus, начиная с R16.

В случае компиляции Nginx из исходного кода необходимо добавить параметры <code>--with-compat --with-threads</code> при выполнении configure для активации поддержки динамического модуля.

### Подключите репозитории Nginx<sub>опционально</sub> и Nemesida WAF:

Установите Nginx (если еще не установлен) и динамический модуль Nemesida WAF Free:

<details>
  <summary>Debian 9</summary>

Подключите репозитории Nginx и Nemesida WAF:

<pre>
# echo "deb http://nginx.org/packages/debian/ stretch nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://repository.pentestit.ru/nw/debian stretch non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Произведите установку пакетов:

<pre>
# apt update && apt upgrade
# apt install nginx
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.5 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# apt install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Debian 10</summary>

Подключите репозитории Nginx и Nemesida WAF:

<pre>
# echo "deb http://nginx.org/packages/debian/ buster nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://repository.pentestit.ru/nw/debian buster non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Произведите установку пакетов:

<pre>
# apt update && apt upgrade
# apt install nginx
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.7 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# apt install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Ubuntu 16.04</summary>

<pre>
# apt install apt-transport-https
</pre>

Подключите репозитории Nginx и Nemesida WAF:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ xenial nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu xenial non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Подключите репозиторий Python 3.6:

<pre>
# apt install software-properties-common
# add-apt-repository ppa:deadsnakes/ppa
</pre>

Произведите установку пакетов:

<pre>
# apt update && apt upgrade
# apt install python3.6 python3.6-dev nginx librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc curl rabbitmq-server
# curl https://bootstrap.pypa.io/get-pip.py | python3.6
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>
</details>

<details>
  <summary>Ubuntu 18.04</summary>

<pre>
# apt install apt-transport-https
</pre>

Подключите репозитории Nginx и Nemesida WAF, произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ bionic nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu bionic non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install python3-pip python3-dev python3-setuptools nginx librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>

</details>

<details>
  <summary>Ubuntu 20.04</summary>

Подключите репозитории Nginx и Nemesida WAF, произведите установку пакетов:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ focal nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu focal non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install python3.8 python3-pip python3.8-dev python3-setuptools nginx librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.8 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>
</details>

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

Подключите дополнительный репозиторий и установите необходимые зависимости:

<pre>
# rpm -Uvh https://repository.pentestit.ru/nw/centos/nwaf-release-centos-7-1-6.noarch.rpm
# yum update
# yum install epel-release
</pre>

Подключите репозиторий Nginx и произведите установку пакетов:

<pre>
# rpm -Uvh https://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
# yum update
# yum install nginx
# yum install python36-pip python36-devel systemd openssl librabbitmq libcurl-devel gcc dmidecode rabbitmq-server
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# yum install nwaf-dyn-1.18
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

Произведите установку пакетов:

<pre>
# dnf update
# dnf install nginx
# dnf install python3-pip python3-devel openssl rabbitmq-server librabbitmq libcurl-devel gcc dmidecode systemd
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# dnf install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).

</details>

<details>
  <summary>CentOS 8</summary>

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

Произведите установку пакетов:

<pre>
# dnf update
# dnf install nginx
# dnf install python3-pip python3-devel openssl rabbitmq-server librabbitmq libcurl-devel gcc dmidecode systemd
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# dnf install nwaf-dyn-1.18
</pre>

где 1.18 — версия установленного Nginx. Например, пакет динамического модуля nwaf-dyn-1.12 предназначен для работы с Nginx версии 1.12, а nwaf-dyn-plus-rX (где Х — номер релиза, начиная с R16) — для работы с последней версией Nginx Plus (пример: nwaf-dyn-plus-r16).
</details>

## Базовая настройка

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

Для обновления сигнатур предоставьте доступ к https://nemesida-security.com. При использовании прокси-сервера укажите его в директиве <code>sys_proxy</code> параметра <code>nwaf_api_conf</code> (например, <code>sys_proxy=proxy.example.com:3128</code>).

Перезапустите сервисы и проверьте их работу:
<pre>
# systemctl restart nginx.service nwaf_update.service
# systemctl status nginx.service nwaf_update.service
</pre>

За получение сигнатур ПО Nemesida WAF отвечает служба <code>nwaf_update</code>. Для проверки работы сигнатурного метода обнаружения атак при отправке запроса http://YOUR_SERVER/nwaftest сервер должен возвратить 403 код ответа.

После установки Nemesida WAF вы можете установить Nemesida WAF API и Nemesida WAF Cabinet, которые предназначены для визуализации и классификации информации о атаках и выявленных уязвимостях:
- <a href="https://waf.pentestit.ru/manuals/5611">Nemesida WAF API</a>
- <a href="https://waf.pentestit.ru/manuals/1446">Nemesida WAF Cabinet</a>

Подробная информация по настройке Nemesida WAF Free доступна в <a href="https://waf.pentestit.ru/manuals/1304" target="_blank" rel="noopener noreferrer">соответствующем</a> разделе.

## Ссылки:

#### Nemesida WAF Free
- Documentation (RU): https://waf.pentestit.ru/about/2511
- Documentation (EN): https://nemesida-waf.com/about/1701

#### Nemesida WAF (коммерческая версия)
- Documentation (RU): https://waf.pentestit.ru/category/manuals
- Documentation (EN): https://nemesida-waf.com/category/manuals

#### Virtual Appliance & Docker images
- Docker image: https://nemesida-waf.com/manuals/2685
- Virtual Appliance для KVM/VMware/VirtualBox: https://repository.pentestit.ru/vm/NemesidaWAF-VA.zip

#### Прочее
- Форум: https://forum.nemesida-security.com
- Набор сигнатур (автообновление): https://rlinfo.nemesida-security.com
- Демонстрационный стенд: https://demo.lk.nemesida-security.com (demo@pentestit.ru / pentestit)
