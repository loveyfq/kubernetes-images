FROM bitfusion-base:0.1

RUN apt install curl -y
RUN \
  mkdir -p /goroot && \
  curl https://storage.googleapis.com/golang/go1.9.linux-amd64.tar.gz | tar xzvf - -C /goroot --strip-components=1
ENV GOROOT /goroot
ENV GOPATH /gopath
ENV PATH $GOROOT/bin:$GOPATH/bin:$PATH

WORKDIR /gopath/src/bitfusion-device-plugin

COPY . .
RUN go build -o bitfusion-device-plugin
RUN cp bitfusion-device-plugin /usr/bin/bitfusion-device-plugin \
  && cp *.sh /usr/bin

CMD ["./start.sh"]
