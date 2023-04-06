FROM golang as builder
RUN go env -w GO111MODULE=off
RUN go get github.com/codegangsta/negroni
RUN go get github.com/gorilla/mux github.com/xyproto/simpleredis
COPY main.go .
RUN go build main.go

#FROM busybox:ubuntu-14.04
FROM busybox:glibc

COPY --from=builder /go//main /app/guestbook

ADD public/index.html /app/public/index.html
ADD public/script.js /app/public/script.js
ADD public/style.css /app/public/style.css
ADD public/jquery.min.js /app/public/jquery.min.js

RUN echo "nobody:x:1:1:nobody:/:/bin/sh" >> /etc/passwd
RUN echo "nobody:x:1:" >> /etc/group

WORKDIR /app
CMD ["./guestbook"]
EXPOSE 3000
