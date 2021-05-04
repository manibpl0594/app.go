FROM alpine

WORKDIR /app

RUN apk update && apk add wget

ADD https://github.com/aquasecurity/trivy/releases/download/v0.16.0/trivy_0.16.0_Linux-64bit.tar.gz .

RUN tar -xvf trivy_0.16.0_Linux-64bit.tar.gz

ENTRYPOINT ["./trivy"]
