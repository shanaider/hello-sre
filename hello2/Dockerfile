FROM golang:1.18-alpine as builder

RUN apk update

WORKDIR /app

COPY go.mod ./
COPY go.sum ./
RUN go mod download

COPY *.go ./

RUN go build -o /go/bin/my-app


# Runtime image
FROM alpine AS base
COPY --from=builder /go/bin/my-app /go/bin/my-app

ENV GO_ENV=production
ENV REDIS_HOST="localhost:6379"
ENV REDIS_PASSWORD="password"
ENV REDIS_DB="0"

EXPOSE 8000

ENTRYPOINT ["/go/bin/my-app"]