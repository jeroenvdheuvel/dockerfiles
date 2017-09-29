FROM alpine:3.6

RUN apk add --no-cache curl && \
    curl -L -o /tmp/nzbget.run https://github.com/nzbget/nzbget/releases/download/v19.1/nzbget-19.1-bin-linux.run && \
    chmod +x /tmp/nzbget.run && \
    /tmp/nzbget.run --destdir /nzbget && \
    sed -i 's/^ControlPassword=.*/ControlPassword=/' /nzbget/nzbget.conf 

FROM scratch

COPY --from=0 /nzbget /nzbget

EXPOSE 6789

CMD ["/nzbget/nzbget", "-s", "-o", "outputmode=log"]
