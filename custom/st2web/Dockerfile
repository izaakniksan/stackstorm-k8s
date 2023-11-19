FROM stackstorm/st2web:3.8.0

# Custom workaround for proxy auth:
#   https://github.com/StackStorm/st2/pull/6049

COPY st2.conf-http.patch /tmp
RUN patch /etc/nginx/conf.d/st2-http.template < /tmp/st2.conf-http.patch

COPY auth.html /opt/stackstorm/static/webui/