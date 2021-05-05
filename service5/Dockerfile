FROM golang:alpine
WORKDIR /app
COPY app.go .
RUN go build app.go
CMD ./app
EXPOSE 8888
