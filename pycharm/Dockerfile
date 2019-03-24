FROM debian:stretch

# docker run -it -v /tmp/.X11-unix/:/tmp/.X11-unix/ -e DISPLAY=$DISPLAY --rm marmarm/pycharm:ce-2018.3.5

ENV PYCHARM_VERSION=community-2018.3.5
ENV PYCHARM_HOME=/etc/pycharm-${PYCHARM_VERION}

RUN apt-get update &&\
    apt-get install --no-install-recommends -y \
    wget \
    ca-certificates \
    git \
    libxrender1 \
    libxtst6 \
    libfreetype6 \
    python3  &&\
    wget https://download.jetbrains.com/python/pycharm-${PYCHARM_VERSION}.tar.gz -O /tmp/pycharm-${PYCHARM_VERSION}.tar.gz && \
    mkdir ${PYCHARM_HOME} && tar -xzvf /tmp/pycharm-${PYCHARM_VERSION}.tar.gz -C ${PYCHARM_HOME} --strip=1 &&\
    rm -rf /var/lib/apt-lists; rm -r /tmp/pycharm-${PYCHARM_VERSION}.tar.gz; apt-get autoremove -y

# Add the pycharm executable path  to PATH
ENV PATH="${PYCHARM_HOME}/bin/:${PATH}"

RUN useradd -ms /bin/bash  pcuser

USER pcuser

ENV PYCHARM_VERSION=community-2018.3.5
ENV PYCHARM_HOME=/etc/pycharm-${PYCHARM_VERION}

# Add the pycharm executable path  to PATH of pcuser
ENV PATH="${PYCHARM_HOME}/bin/:${PATH}"

CMD ["/bin/bash"]

