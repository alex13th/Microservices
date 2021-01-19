FROM golang as builder

RUN mkdir /app

COPY . /app

WORKDIR /app
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o sum_server .

FROM scratch

COPY --from=builder /app/sum_server /

EXPOSE 8080

CMD ["/sum_server"]