FROM bohrok/ubuntu20

RUN git clone https://github.com/rjust/defects4j ~/defects4j
WORKDIR /root/defects4j
RUN cpan --installdeps .
RUN ./init.sh
ENV PATH=$PATH:"/root/defects4j"/framework/bin
RUN defects4j info -p Lang
RUN apt install locales
RUN localedef -f UTF-8 -i en_US en_US.UTF-8
RUN locale-gen en_US.UTF-8
RUN locale -a
ENV LC_ALL=en_US.UTF-8
RUN locale
RUN apt install maven
RUN curl -s "https://get.sdkman.io" | bash
RUN source "/root/.sdkman/bin/sdkman-init.sh"
RUN sdk install gradle 7.2

RUN apt install -y apt-transport-https
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
RUN add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/'
RUN apt install -y r-base
RUN R --version

WORKDIR /root

ENTRYPOINT [ "/bin/bash" ]