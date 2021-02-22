# Nemesida WAF Free - free WAF for NGINX

Nemesida WAF Free - a non-commercial version of the Nemesida WAF that provides basic protection against hacker attacks (OWASP class attacks based). Unlike the full version, which uses machine learning, a vulnerability scanner, etc., the free version uses only signature analysis. Nemesida WAF Free has its <a href="https://rlinfo.nemesida-security.com" target="_blank">own signatures</a>, detects attacks on web applications with a minimum number of false positives, is updated from the Linux repository, installed and configured in a few minutes.

![Nemesida WAF Cabinet](https://nemesida-waf.com/wp-content/uploads/2019/08/1.png)

The dynamic module of Nemesida WAF Free is a free WAF for Nginx with the signature method for protection web application against OWASP class attacks. Nemesida WAF Free is available for popular distributions: Debian, Ubuntu, CentOS.

## Nemesida WAF Features:

- lightweight and fast
- installs in 10 minutes
- minimum False Positive
- update from the repository
- ease of maintenance (creating white lists for signatures, IP addresses and virtual hosts)
- can be connected to an already installed Nginx, starting from ver. 1.12

## Installation

Installation and setup of Nemesida WAF Free takes only a few minutes. The dynamic module Nemesida WAF is available for:
- Nginx stable from 1.12
- Nginx mainline from 1.17
- Nginx Plus starting from R16.

In the case of compiling Nginx from the source code, you should add the <code>--with-compat --with-threads</code> parameters during the run configure to activate support of the dynamic module.

### Add the Nginx and Nemesida WAF repositories:

Install Nginx (if necessary) and Nemesida WAF Free:

<details>
  <summary>Debian 9</summary>

Add the Nginx and Nemesida WAF repositories:

<pre>
# echo "deb http://nginx.org/packages/debian/ stretch nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://repository.pentestit.ru/nw/debian stretch non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Make the installation of the packages:

<pre>
# apt update && apt upgrade
# apt install nginx
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev gcc rabbitmq-server
# python3.5 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# apt install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (e.g. nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Debian 10</summary>

Add the Nginx and Nemesida WAF repositories:

<pre>
# echo "deb http://nginx.org/packages/debian/ buster nginx" > /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb https://repository.pentestit.ru/nw/debian buster non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Make the installation of the packages:

<pre>
# apt update && apt upgrade
# apt install nginx
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev gcc rabbitmq-server
# python3.7 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# apt install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (e.g. nwaf-dyn-plus-r16).
</details>

<details>
  <summary>Ubuntu 16.04</summary>

<pre>
# apt install apt-transport-https
</pre>

Add the Nginx and Nemesida WAF repositories:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ xenial nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu xenial non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
</pre>

Add the Python 3.6 repository:

<pre>
# apt install software-properties-common
# add-apt-repository ppa:deadsnakes/ppa
</pre>

Install the packages:

<pre>
# apt update && apt upgrade
# apt install python3.6 python3.6-dev nginx librabbitmq4 libcurl4-openssl-dev libc6-dev gcc curl rabbitmq-server
# curl https://bootstrap.pypa.io/get-pip.py | python3.6
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>
</details>

<details>
  <summary>Ubuntu 18.04</summary>

<pre>
# apt install apt-transport-https
</pre>

Add the Nginx and Nemesida WAF repositories, install the packages:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ bionic nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu bionic non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install python3-pip python3-dev python3-setuptools nginx librabbitmq4 libcurl4-openssl-dev libc6-dev gcc rabbitmq-server
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>

</details>

<details>
  <summary>Ubuntu 20.04</summary>

Add the Nginx and Nemesida WAF repositories, install the packages:

<pre>
# echo "deb http://nginx.org/packages/ubuntu/ focal nginx"> /etc/apt/sources.list.d/nginx.list
# wget -O- https://nginx.org/packages/keys/nginx_signing.key | apt-key add -
# echo "deb [arch=amd64] https://repository.pentestit.ru/nw/ubuntu focal non-free" > /etc/apt/sources.list.d/NemesidaWAF.list
# wget -O- https://repository.pentestit.ru/nw/gpg.key | apt-key add -
# apt update && apt upgrade
# apt install python3.8 python3-pip python3.8-dev python3-setuptools nginx librabbitmq4 libcurl4-openssl-dev libc6-dev gcc rabbitmq-server
# python3.8 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
</pre>
</details>

<details>
  <summary>CentOS 7</summary>

Configure the SELinux policy or deactivate it with the command:

<pre>
# setenforce 0
</pre>

and bring the file <code>/etc/selinux/config</code> to the form:

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

Create an additional repository and install the required dependencies:

<pre>
# rpm -Uvh https://repository.pentestit.ru/nw/centos/nwaf-release-centos-7-1-6.noarch.rpm
# yum update
# yum install epel-release
</pre>

Add the Nginx repository and install the packages:

<pre>
# rpm -Uvh https://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
# yum update
# yum install nginx
# yum install python36-pip python36-devel systemd openssl librabbitmq libcurl-devel gcc rabbitmq-server
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# yum install nwaf-dyn-1.18
</pre>

Install the package:

<pre>
# dnf install dnf-utils
</pre>

Add the Nginx repository, changing file/etc/yum.repos.d/nginx.repo:

<pre>
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true
</pre>

Install the packages:

<pre>
# dnf update
# dnf install nginx
# dnf install python3-pip python3-devel openssl rabbitmq-server librabbitmq libcurl-devel gcc systemd
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# dnf install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (e.g. nwaf-dyn-plus-r16).

</details>

<details>
  <summary>CentOS 8</summary>

Configure the SELinux policy or deactivate it with the command:

<pre>
# setenforce 0
</pre>

and bring the file <code>/etc/selinux/config</code> to the form:

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

Install the package:

<pre>
# dnf install dnf-utils
</pre>

Add the Nginx repository, changing file/etc/yum.repos.d/nginx.repo:

<pre>
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true
</pre>

Install the packages:

<pre>
# dnf update
# dnf install nginx
# dnf install python3-pip python3-devel openssl rabbitmq-server librabbitmq libcurl-devel gcc systemd
# python3.6 -m pip install --no-cache-dir cython pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode fsspec func_timeout url-normalize
# dnf install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (e.g. nwaf-dyn-plus-r16).
</details>

## Settings up

Add the path to the file with the dynamic module Nemesida WAF and bring the parameters below in the configuration file <code>/etc/nginx/nginx.conf</code> to the form:

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

To update signatures, provide access to https://nemesida-security.com. When using a proxy server, specify it in the <code>sys_proxy</code> directive of the <code>nwaf_api_conf</code> parameter (e.g. <code>sys_proxy=proxy.example.com:3128</code>).

Restart the server and test:
<pre>
# systemctl restart nginx.service nwaf_update.service
# systemctl status nginx.service nwaf_update.service
</pre>

The service <code>nwaf_update</code> is responsible for obtaining signatures of the Nemesida WAF software. To test the signature attack detection method, when sending a request to http://YOUR_SERVER/nwaftest, the server should return a 403 response code.

After Nemesida WAF installation you can install Nemesida WAF API and Nemesida WAF Cabinet, which is intended to visualise and classify the information about attacks and identified vulnerabilities:
- <a href="https://nemesida-waf.com/manuals/2407">Nemesida WAF API</a>
- <a href="https://nemesida-waf.com/manuals/1612">Nemesida WAF Cabinet</a>

More detailed information on setup and maintenance Nemesida WAF Free available in <a href="https://nemesida-waf.com/manuals/1285" target="_blank" rel="noopener noreferrer">guide</a>.

## Related links:

#### Free version
- Documentation (RU): https://waf.pentestit.ru/about/2511
- Documentation (EN): https://nemesida-waf.com/about/1701

#### Full version
- Documentation (RU): https://waf.pentestit.ru/category/manuals
- Documentation (EN): https://nemesida-waf.com/category/manuals

#### Virtual Appliance & Docker images
- Docker image: https://nemesida-waf.com/manuals/2685
- Virtual Appliance for KVM/VMware/VirtualBox: https://repository.pentestit.ru/vm/NemesidaWAF-VA.zip

#### Misc.
- Forum: https://forum.nemesida-security.com
- Signature Set (auto update): https://rlinfo.nemesida-security.com
- Demonstration stand: https://demo.lk.nemesida-security.com (demo@pentestit.ru / pentestit)
