Nemesida WAF Free provides the base web application security against OWASP class attacks based on the signature method. Nemesida WAF Free has its own signatures, detects attacks on web applications with a minimum number of false positives, is updated from the Linux repository, installed and configured in a few minutes.

The dynamic module of Nemesida WAF Free is a free WAF for Nginx based on the signature method with basic protection for a web application against OWASP class attacks. Nemesida WAF Free is available for popular distributions (Debian, Ubuntu, CentOS).

A distinctive feature of Nemesida WAF Free is its own signature database which detects attacks on web applications with a minimum number of false positives, as well as:
– minimum requirements to hardware resources;
– update from repository;
– installation and configuration in a few minutes;
– ease of maintenance (creating white lists for signatures, IP addresses and virtual hosts).

# Installation

Installation and setup of Nemesida WAF Free takes only a few minutes. The dynamic module Nemesida WAF is available for:
- Nginx stable from 1.12;
- Nginx mainline from 1.17;
- Nginx Plus.

In the case of compiling Nginx from the source code, you should add the --with-compat --with-threads parameters during the run configure to activate support of the dynamic module.

## Add the Nginx and Nemesida WAF repositories:

### Debian 9
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
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.5 -m pip install --no-cache-dir pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode 
# apt install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (for example: nwaf-dyn-plus-r16).

### Debian 10
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
# apt install python3-pip python3-dev python3-setuptools librabbitmq4 libcurl4-openssl-dev libc6-dev dmidecode gcc rabbitmq-server
# python3.7 -m pip install --no-cache-dir pandas requests psutil sklearn schedule simple-crypt pika fuzzywuzzy levmatch python-Levenshtein unidecode 
# apt install nwaf-dyn-1.18
</pre>

where 1.18 is the version of the installed Nginx. For example, package of the dynamic module nwaf-dyn-1.12 is intended for work with Nginx version 1.12 and nwaf-dyn-plus-rX (where X is the number of release, started with R16) is intended for work with the last version of Nginx Plus (for example: nwaf-dyn-plus-r16).

## Settings up

Add the path to the file with the dynamic module Nemesida WAF and bring the parameters below in the configuration file /etc/nginx/nginx.conf to the form:

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

To update signatures, provide access to https://nemesida-security.com. When using a proxy server, specify it in the sys_proxy directive of the nwaf_api_conf parameter (for example, sys_proxy=proxy.example.com:3128).

Restart the server and test :
<pre>
# systemctl restart nginx.service nwaf_update.service
# systemctl status nginx.service nwaf_update.service
</pre>

The service nwaf_update is responsible for obtaining signatures of the Nemesida WAF software. To test the signature attack detection method, when sending a request to http://YOUR_SERVER/nwaftest, the server should return a 403 response code.
