FROM golang:1.7.5
RUN mkdir -p /go/src/github.com/alexellis/faas/watchdog
WORKDIR /go/src/github.com/alexellis/faas/watchdog

COPY main.go        .
COPY readconfig.go  .
COPY config_test.go .
COPY requesthandler_test.go .
COPY types types

RUN go test

RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o watchdog .

RUN GOARM=6 GOARCH=arm CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o watchdog-armhf .
