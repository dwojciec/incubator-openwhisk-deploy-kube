FROM registry.access.redhat.com/rhscl/nginx-112-rhel7:latest

USER root

RUN mkdir -p /opt/app-root/etc/nginx/cli/go/download/linux/386/ && \
    mkdir -p /opt/app-root/etc/nginx/cli/go/download/linux/amd64/ && \
    mkdir -p /opt/app-root/etc/nginx/cli/go/download/mac/386/ && \
    mkdir -p /opt/app-root/etc/nginx/cli/go/download/mac/amd64/ && \
    mkdir -p /opt/app-root/etc/nginx/cli/go/download/windows/386 && \
    chown -R 1001:0 /opt/app-root

# Download all of the OpenWhisk CLIs
ADD https://github.com/apache/incubator-openwhisk-cli/releases/download/latest/OpenWhisk_CLI-latest-linux-386.tgz /etc/nginx/cli/go/download/linux/386/wsk.tgz
ADD https://github.com/apache/incubator-openwhisk-cli/releases/download/latest/OpenWhisk_CLI-latest-linux-amd64.tgz /etc/nginx/cli/go/download/linux/amd64/wsk.tgz
#ADD https://github.com/apache/incubator-openwhisk-cli/releases/download/latest/OpenWhisk_CLI-latest-mac-386.zip /etc/nginx/cli/go/download/mac/386/wsk.zip
#ADD https://github.com/apache/incubator-openwhisk-cli/releases/download/latest/OpenWhisk_CLI-latest-mac-amd64.zip /etc/nginx/cli/go/download/mac/amd64/wsk.zip
#ADD https://github.com/apache/incubator-openwhisk-cli/releases/download/latest/OpenWhisk_CLI-latest-windows-386.zip /etc/nginx/cli/go/download/windows/386/wsk.zip

RUN chown -R 1001:0 /opt/app-root && \
    chmod -R a+rwx  /opt/app-root && \
    rpm-file-permissions
# Untar all of the files
RUN tar zxvf /etc/nginx/cli/go/download/linux/386/wsk.tgz -C /etc/nginx/cli/go/download/linux/386
RUN tar zxvf /etc/nginx/cli/go/download/linux/amd64/wsk.tgz -C /etc/nginx/cli/go/download/linux/amd64
#RUN unzip /etc/nginx/cli/go/download/mac/386/wsk.zip -d /etc/nginx/cli/go/download/mac/386
#RUN unzip /etc/nginx/cli/go/download/mac/amd64/wsk.zip -d /etc/nginx/cli/go/download/mac/amd64
#RUN unzip /etc/nginx/cli/go/download/windows/386/wsk.zip -d /etc/nginx/cli/go/download/windows/386

# Remove extra zip file
RUN rm /etc/nginx/cli/go/download/linux/386/wsk.tgz
RUN rm /etc/nginx/cli/go/download/linux/amd64/wsk.tgz
#RUN rm /etc/nginx/cli/go/download/mac/386/wsk.zip
#RUN rm /etc/nginx/cli/go/download/mac/amd64/wsk.zip
#RUN rm /etc/nginx/cli/go/download/windows/386/wsk.zip

USER 1001
