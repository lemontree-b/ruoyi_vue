FROM node:22-alpine AS builder
ENV  CODE=/app/code/
WORKDIR  ${CODE}
COPY  . ./

RUN set -xe ; \
    npm i --registry=https://registry.npmmirror.com  ; \
    npm run build:prod
FROM nginx:1.28-alpine
LABEL author="lidao996"  desc="前端 china"
ENV  CODE=/app/code/

COPY  --from=builder  ${CODE}/dist/   /usr/share/nginx/html/
COPY  ./docker/nginx.conf     /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx","-g","daemon off;"]

