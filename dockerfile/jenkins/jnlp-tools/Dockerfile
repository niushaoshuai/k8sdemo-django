FROM alpine
LABEL maintainer="inspur_lyx@hotmail.com"
USER root

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories &&     apk update &&     apk add  --no-cache openrc docker git curl tar gcc g++ make     bash shadow openjdk8 python3 python3-dev py-pip openssl-dev libffi-dev     libstdc++ harfbuzz nss freetype ttf-freefont chromium chromium-chromedriver &&     mkdir -p /root/.kube &&     usermod -a -G docker root

COPY requirements.txt /
COPY config /root/.kube/

RUN pip install -U pip
RUN pip install -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com -r /requirements.txt

RUN rm -rf /var/cache/apk/* &&     rm -rf ~/.cache/pip
#-----------------安装 kubectl--------------------#
RUN mkdir /lib64
RUN ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
COPY kubectl /usr/bin/
RUN chmod +x /usr/bin/kubectl
# ------------------------------------------------#
