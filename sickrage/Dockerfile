FROM alpine:3.6

ENV SICKRAGE_VERSION 2017.06.05-1

RUN apk add --no-cache python python-dev py-pip py-libxml2 py-lxml ca-certificates \
            curl make gcc g++ openssl-dev libffi-dev unrar

RUN pip --no-cache-dir install pyopenssl cheetah babel

RUN mkdir /opt && \
    curl -L -o /opt/sickrage.tar.gz https://github.com/SickRage/SickRage/archive/v$SICKRAGE_VERSION.tar.gz && \
    tar -xzvf /opt/sickrage.tar.gz -C /opt/ && \
    rm /opt/sickrage.tar.gz && \
    mv /opt/SickRage-$SICKRAGE_VERSION /opt/sickrage

CMD ["/usr/bin/python", "/opt/sickrage/SickBeard.py", "--nolaunch"]

# TODO: Try to use sickrage/setup.py to install missing Python packages
