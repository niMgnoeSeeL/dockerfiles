FROM bohrok/ubuntu20

RUN git clone https://github.com/rjust/defects4j ~/defects4j
WORKDIR /root/defects4j
RUN cpan --installdeps .
RUN ./init.sh
ENV PATH=$PATH:"/root/defects4j"/framework/bin
RUN defects4j info -p Lang