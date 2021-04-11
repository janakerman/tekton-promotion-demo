FROM alpine
#FROM alpine/git:v2.26.2

RUN mkdir /ghcli
WORKDIR /ghcli
RUN wget https://github.com/cli/cli/releases/download/v1.8.1/gh_1.8.1_linux_386.tar.gz -O ghcli.tar.gz
RUN tar --strip-components=1 -xf ghcli.tar.gz
ENTRYPOINT ["bin/gh"]