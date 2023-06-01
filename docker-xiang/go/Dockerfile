###############################################################################
#                                compile
###############################################################################
FROM golang:alpine3.16 as compiler

ENV WORKDIR /app
ENV GO111MODULE on

RUN apk update && apk upgrade && \
    # 调时区程序,k8s启动时会调用
    apk add tzdata && \
    apk add --no-cache git openssh && \
    rm -rf /var/cache/apk/*


COPY . $WORKDIR

RUN --mount=type=ssh cd $WORKDIR && \
    go build -o main-web main.go && \
    chmod +x main-web

###############################################################################
#                                install
###############################################################################
FROM alpine:3.16

ENV WORKDIR /app

RUN apk update && apk upgrade && \
    apk add tzdata && \
    apk add curl && \
    rm -rf /var/cache/apk/*

COPY --from=compiler $WORKDIR/main-web $WORKDIR/main-web
COPY --from=compiler $WORKDIR/main-crontab $WORKDIR/main-crontab
COPY --from=compiler $WORKDIR/main-worker $WORKDIR/main-worker

ADD ./manifest/config/config.prod.yaml $WORKDIR/manifest/config/config.prod.yaml
ADD ./manifest/config/config.pre.yaml $WORKDIR/manifest/config/config.pre.yaml

ADD ./resource $WORKDIR/resource

RUN mkdir -p $WORKDIR/logs

EXPOSE 8003

WORKDIR $WORKDIR

CMD top

