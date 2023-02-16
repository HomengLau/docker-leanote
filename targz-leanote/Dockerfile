FROM --platform=amd64 ubuntu
LABEL org.opencontainers.image.authors="homeng@homeng.net"
ENV TZ=Asia/Shanghai
ENV DEBIAN_FRONTEND noninteractive

ADD run.sh /root/
# ADD leanote-linux-amd64-v2.6.1.bin.tar.gz /root/
# ADD wkhtmltox-0.12.4_linux-generic-amd64.tar.xz /root/
# ADD mongodb-database-tools.tar /root/
RUN set -ex; \
    # ls /root/; \
    # ls /root/mongodb-database-tools-ubuntu2204-x86_64-100.6.1/; \
    # ls /etc/; \
    # ls /prop/; \
    # cat /etc/issue; \
    #更换源
    # sed -i "s@ http://.*archive.ubuntu.com@http://security.ubuntu.com @g" /etc/apt/sources.list; \
    # sed -i "s@http://.*security.ubuntu.com@https://mirrors.tuna.tsinghua.edu.cn@g" /etc/apt/sources.list; \
    # cat /etc/apt/sources.list; \
    # cat /etc/os-release; \
    #清除缓存
    apt-get clean; \
    #开始安装依赖
    apt-get update; \
    #apt-cache search mongodb-org; \
    # apt-cache search ssl; \
    apt-get install -y wget tar && \
    #download wkhtmltopdf
    echo "download wkhtmltopdf"; \
    #wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz; \
    wget ftp://NasIP/wkhtmltox-0.12.4_linux-generic-amd64.tar.gz && \
    ls -al && \
    tar -xzvf wkhtmltox-0.12.4_linux-generic-amd64.tar.gz && \
    ls -al && \
    echo "download leanote sources bin"; \
    wget ftp://NasIP/leanote-linux-amd64-v2.6.1.bin.tar.gz && \
    ls -al && \
    tar -xzvf leanote-linux-amd64-v2.6.1.bin.tar.gz && \
    ls ./ && \
    apt-get install -y --no-install-recommends apt-utils libssl-dev; \
    # install font
    apt-get install -y --no-install-recommends xvfb libXrender* libfontconfig*; \
    apt-get install -f -y --no-install-recommends\
        fonts-arphic-bkai00mp \
        fonts-arphic-bsmi00lp \
        fonts-arphic-gbsn00lp \
        fonts-arphic-gkai00mp \
        fonts-arphic-ukai \
        fonts-arphic-uming \
        ttf-wqy-zenhei \
        ttf-wqy-microhei \
        # ttf-dejavu ttf-droid ttf-freefont ttf-liberation ttf-ubuntu-font-family \
        xfonts-wqy; \
    # apk add --no-cache tzdata libgcc libstdc++ libx11 glib  libxext libintl; \
    # chmod +x /root/mongodb-database-tools-ubuntu2204-x86_64-100.6.1/bin/*; \
    # cp /root/mongodb-database-tools-ubuntu2204-x86_64-100.6.1/bin/* /usr/local/bin/; \
    ls /root/; \
    # ls /root/mongodb-database-tools-ubuntu2204-x86_64-100.6.1/; \
    # rm -rf /root/mongodb-database-tools-ubuntu2204-x86_64-100.6.1/; \
    mv /wkhtmltox/bin/wkhtmltopdf /usr/local/bin/wkhtmltopdf; \
    rm -rf leanote-linux-amd64-v2.6.1.bin.tar.gz && \
    rm -rf wkhtmltox-0.12.4_linux-generic-amd64.tar.gz && \
    chmod +x /usr/local/bin/wkhtmltopdf; \    
    mkdir /data/; \
    mv /leanote /data/leanote; \
    echo "/data/leanote/bin/run.sh"; \
    # cat /data/leanote/bin/run.sh;\
    echo "/root/run.sh"; \
    # cat /root/run.sh; \
    chmod a+x /root/run.sh; \
    chmod +x /data/leanote/bin/run.sh; \
    echo 'export QT_QPA_PLATFORM=offscreen' >> ~/.bashrc; \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime; \
    echo $TZ > /etc/timezone
EXPOSE 9000
# # CMD ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && /bin/bash /root/run.sh
CMD /bin/sh /root/run.sh
