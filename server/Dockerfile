FROM golang:1.21 as builder
WORKDIR /go/src/app
COPY server/ ./
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -v -o app

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /go/src/app/app .
EXPOSE 8080
CMD ["./app"]
