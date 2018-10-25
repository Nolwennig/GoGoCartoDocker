FROM php56_fpm

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -y wget mysql-client git vim bash-completion nano ruby-full libssl1.0.0

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php -r "if (hash_file('SHA384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && php composer-setup.php && php -r "unlink('composer-setup.php');"

RUN wget -qO- https://deb.nodesource.com/setup_8.x | sudo -E bash - && apt-get install -y nodejs

ADD bash.bashrc /etc/bash.bashrc
ADD .bashrc /root/.bashrc

WORKDIR /var/www/html/GoGoCarto/

ENTRYPOINT []

CMD ["/usr/bin/watch", "ls"]
