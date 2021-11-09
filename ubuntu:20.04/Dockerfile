FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=America/Los_Angeles
RUN apt update && apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
RUN apt install -y git tmux vim
RUN apt install -y software-properties-common
RUN apt install -y subversion perl libdbi-perl
RUN apt install -y zip

# pyenv
RUN git clone https://github.com/pyenv/pyenv.git ~/.pyenv
ENV PYENV_ROOT="/root/.pyenv"
ENV PATH="$PYENV_ROOT/bin:$PATH"
RUN eval "$(pyenv init --path)"
RUN eval "$(pyenv init -)"
RUN pyenv install 3.10.0
RUN pyenv global 3.10.0
RUN echo 'export PYENV_ROOT="/root/.pyenv"' >> ~/.bashrc
RUN echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(pyenv init --path)"' >> ~/.bashrc
RUN echo 'eval "$(pyenv init -)"' >> ~/.bashrc

# jenv
RUN git clone https://github.com/jenv/jenv.git ~/.jenv
ENV PATH="/root/.jenv/bin:$PATH"
RUN eval "$(jenv init -)"
RUN echo 'export PATH="/root/.jenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(jenv init -)"' >> ~/.bashrc

RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean;
RUN apt-get update && \
    apt-get install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;
RUN jenv add /usr/lib/jvm/java-8-openjdk-amd64
RUN jenv global 1.8

ENTRYPOINT [ "/bin/bash" ]