FROM nginxinc/nginx-unprivileged:1-alpine

COPY ./deault.conf.tpl /etc/nginx/deault.conf.tpl
COPY ./uwsgi_params /etc/nginx/uwsgi_params
COPY ./run.sh /run.sh

ENV LISTEN_PORT=8000
ENV APP_HOST=app
ENV APP_PORT=9000

USER root

RUN mdir -p /vol/static && \
    chmod 755 /vol/static && \
    touch /etc/nginx/conf.d/deault.conf && \
    chown nginx:nginx /etc/nginx.conf.d/deault.conf && \
    chmod +x /run.sh

VOLUME /vol/static

USER nginx

CMD ["run.sh"]