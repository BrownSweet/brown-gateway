FROM nginx:1.27.3-alpine

ARG TZ
ARG CONTAINER_PACKAGE_URL

# 资源替换 更换镜像
RUN if [ ${CONTAINER_PACKAGE_URL} ]; then sed -i "s/dl-cdn.alpinelinux.org/${CONTAINER_PACKAGE_URL}/g" /etc/apk/repositories; fi

RUN if [ ${TZ} ]; then apk add --no-cache --virtual .time-deps tzdata && cp -r "/usr/share/zoneinfo/${TZ}" /etc/localtime && echo "${TZ}" > /etc/timezone && apk del .time-deps; fi

RUN apk add --no-cache certbot;
WORKDIR /www
