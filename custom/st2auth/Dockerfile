FROM stackstorm/st2auth:3.8.0

# Custom workaround for proxy auth:
#   https://github.com/StackStorm/st2/pull/6049.patch
#   https://github.com/StackStorm/st2/pull/6041.patch

COPY auth.py.patch /tmp
COPY handlers.py.patch /tmp
COPY openapi.yaml.j2.patch /tmp
USER root
RUN patch /opt/stackstorm/st2/lib/python3.8/site-packages/st2auth/controllers/v1/auth.py < /tmp/auth.py.patch && \
    patch /opt/stackstorm/st2/lib/python3.8/site-packages/st2auth/handlers.py < /tmp/handlers.py.patch && \
    patch /opt/stackstorm/st2/lib/python3.8/site-packages/st2common/openapi.yaml.j2 < /tmp/openapi.yaml.j2.patch && \
    rm /tmp/auth.py.patch /tmp/handlers.py.patch /tmp/openapi.yaml.j2.patch 
USER st2