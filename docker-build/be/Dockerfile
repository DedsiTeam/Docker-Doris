# 选择基础镜像
FROM openjdk:17-jdk-slim

# 设置环境变量
ENV JAVA_HOME="/usr/local/openjdk-17/"
ENV PATH="/opt/apache-doris/be/bin:$PATH"

# 下载软件至镜像内，可根据需要替换
ADD ./resource/apache-doris-3.0.4-bin-x64.tar.gz /opt/

RUN apt-get update && \
    apt-get install -y default-mysql-client && \
    apt-get clean && \
    mkdir /opt/apache-doris && \
    cd /opt && \
    mv apache-doris-3.0.4-rc02-bin-x64/be /opt/apache-doris/

ADD ./resource/init_be.sh /opt/apache-doris/be/bin
ADD ./resource/start_be.sh /opt/apache-doris/be/bin
RUN chmod 755 /opt/apache-doris/be/bin/init_be.sh
RUN chmod 755 /opt/apache-doris/be/bin/start_be.sh

ENTRYPOINT ["/opt/apache-doris/be/bin/init_be.sh"]