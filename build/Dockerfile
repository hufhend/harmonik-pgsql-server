FROM postgres:13.5
RUN localedef -i cs_CZ -c -f UTF-8 -A /usr/share/locale/locale.alias cs_CZ.UTF-8
ENV LANG cs_CZ.UTF-8
ENV PYTHON_VERSION 3.7.6
RUN apt update && \
    apt install -y wget && \
    wget https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tar.xz && \
    tar -xf Python-${PYTHON_VERSION}.tar.xz && \
    mv Python-${PYTHON_VERSION} /opt/ && \
    apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev curl libbz2-dev -y
RUN cd /opt/Python-${PYTHON_VERSION} && \
    ./configure --enable-optimizations --enable-shared && \
    make && \
    make -j 6 && \
    make altinstall && \
    ldconfig /opt/Python-${PYTHON_VERSION}
RUN python3.7 --version && \
    rm /Python-${PYTHON_VERSION}.tar.xz && rm -rf /tmp/* && \
    rm -rf /opt/Python-${PYTHON_VERSION}/build && \
    rm -rf /usr/lib/gcc \
    
