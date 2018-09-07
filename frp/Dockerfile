FROM alpine:3.7

LABEL maintainer="hpeng526 <hpeng526@gmail.com>"

ENV TIMEZONE    Asia/Shanghai
ENV VERSION     0.21.0
ENV DOWNLOAD    https://github.com/fatedier/frp/releases/download/v${VERSION}/frp_${VERSION}_linux_amd64.tar.gz

RUN apk upgrade --update \
    && apk add curl \
    && curl -sSLO ${DOWNLOAD} \
    && tar -zxvf frp_${VERSION}_linux_amd64.tar.gz \
    && mv frp_${VERSION}_linux_amd64/*.ini /etc \
    && mv frp_${VERSION}_linux_amd64/frp* /usr/local/bin \
    && ln -sf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    && apk del curl \
    && rm -rf frp_* \
        /var/cache/apk/*

CMD [ "frps", "-c", "/etc/frps.ini" ]