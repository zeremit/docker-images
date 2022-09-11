FROM ubuntu:22.04

RUN apt-get update && \
    apt-get dist-upgrade -y && \
    apt-get clean

RUN apt-get install -y wget locales gnupg2 && \
    apt-get clean

RUN echo "deb http://repo.yandex.ru/yandex-disk/deb/ stable main" | tee -a /etc/apt/sources.list.d/yandex-disk.list > /dev/null && wget http://repo.yandex.ru/yandex-disk/YANDEX-DISK-KEY.GPG -O- | apt-key add - && apt-get update && apt-get install -y yandex-disk \
    && apt-get purge -y \
    && apt-get autoremove -y \
    && rm -r /var/lib/apt/lists/* \
    && mkdir /root/Yandex.Disk

RUN echo 'en_US.UTF-8 UTF-8' > /etc/locale.gen && \
    locale-gen --purge en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

CMD ["sh", "-c", "yandex-disk start --no-daemon --dir=/root/Yandex.Disk --exclude-dirs=$exclude_dirs"]