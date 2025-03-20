FROM alpine:latest
RUN apk update && apk add curl bash go parallel
RUN curl https://install.speedtest.net/app/cli/ookla-speedtest-1.2.0-linux-`uname -m`.tgz -o speedtest.tgz && tar -xzf speedtest.tgz && mv speedtest /usr/bin
RUN go install github.com/fullstorydev/grpcurl/cmd/grpcurl@latest
RUN mv ~/go/bin/grpcurl /usr/bin
RUN curl https://raw.githubusercontent.com/Scootter23/starlinkstatus/main/starlinkstatus_client.sh -o /usr/bin/starlinkstatus_client.sh && chmod +x /usr/bin/starlinkstatus_client.sh
RUN speedtest --accept-license --accept-gdpr
COPY --chmod=550 starlinkstatus_client.sh .
ENTRYPOINT ./starlinkstatus_client.sh -k $APIKEY -s -d -i $INTERVAL
