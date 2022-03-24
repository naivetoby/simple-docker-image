FROM jangrewe/gitlab-ci-android

COPY .ossutilconfig /root/.ossutilconfig

RUN apt update && \
    apt install --no-install-recommends -y build-essential software-properties-common && \
    add-apt-repository -y ppa:deadsnakes/ppa && \
    apt install --no-install-recommends -y \
      python3.7 \
      python3.7-dev \
      python3.7-distutils \
      wget \
      gettext-base && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Register the version in alternatives
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.7 1

# Set python 3 as the default python
RUN update-alternatives --set python /usr/bin/python3.7

RUN python3 -V

RUN wget -P /root http://gosspublic.alicdn.com/ossutil/1.7.5/ossutil64 && \
    chmod 755 /root/ossutil64
