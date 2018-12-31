  web:
    image: nginx:latest
    volumes:
      - ${pwd}/site.conf:/etc/nginx/conf.d/site.conf
    ports:
      - "80:80"
    links:
      - phpfpm

  phpfpm:
    image: php:fpm
    volumes:
      - ./code:/usr/share/nginx/html
    ports:
      - "9000:9000"


the links command in web service:
adds the dns name and ip address of phpfm container in its /etc/hosts file

the names of the docker container are in the following format 
<directory name>_<servicename-defined-composefile>_<instance>
dockerphp7fpm_phpfpm_1
