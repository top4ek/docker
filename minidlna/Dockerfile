FROM debian:wheezy

RUN \
    apt-get update && \
    apt-get upgrade && \
    apt-get install -y locales minidlna && \
    echo 'ru_RU.UTF-8 UTF-8' > /etc/locale.gen && \
    locale-gen && \
    /usr/sbin/update-locale LANG=ru_RU.UTF-8 && \
    export LC_ALL=ru_RU.UTF-8 && \
    export LANG=ru_RU.UTF-8 && \
    export LANGUAGE=ru_RU.UTF-8 && \

    echo "Europe/Moscow" > /etc/timezone && \
    dpkg-reconfigure -f noninteractive tzdata && \

    apt-get clean && \
    sed -i 's/media_dir=\/var\/lib\/minidlna/media_dir=\/srv/g' /etc/minidlna.conf && \
    sed -i 's/#inotify=yes/inotify=yes/g' /etc/minidlna.conf && \
    sed -i 's/#friendly_name=/friendly_name=Home-DLNA/g' /etc/minidlna.conf

VOLUME /srv

EXPOSE 1900/udp 8200

CMD /usr/bin/minidlna -d -R -f /etc/minidlna.conf
