FROM debian:buster

RUN apt-get update && apt-get install -y \
    wget \
    vim \
    unzip \
    curl \
    tar \
    openssh-client\
    git \
    apt-transport-https \
    software-properties-common \
    lsb-release \
    ca-certificates \
    build-essential  \
    jq \
    make \
    python3 \
    python3-pip \
    virtualenv \
    libgmp-dev \
    golang-go

RUN pip3 install \
    botocore \
    ansible \
    && ansible-galaxy collection install community.general:1.3.5
    
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - \
    && apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
    && apt-get update && apt-get install -y terraform \
    && rm -rf /var/lib/apt/lists/*

RUN go get -v github.com/ncarlier/webhookd \
    && mv /root/go/bin/webhookd /usr/local/bin \
    && rm -rf /root/go
