FROM golang:1.11 as builder
ARG CGO_ENABLED=0
WORKDIR /go/src/github.com/newrelic/nri-apache
COPY . .
RUN make clean compile

FROM httpd:2.4
COPY --from=builder /go/src/github.com/newrelic/nri-apache/bin /
RUN ln -s /usr/local/apache2/bin/httpd /usr/sbin/httpd
