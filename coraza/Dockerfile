FROM golang:1.22-alpine AS builder
WORKDIR /build
RUN apk add --no-cache git
ENV GIT_TERMINAL_PROMPT=0
ENV GIT_ASKPASS=echo
RUN git clone https://dummy@github.com/corazawaf/coraza-proxy.git .
RUN go build -o coraza-proxy .

FROM alpine:latest
RUN apk add --no-cache ca-certificates
COPY --from=builder /build/coraza-proxy /usr/local/bin/
ENTRYPOINT ["coraza-proxy"]