FROM golang:alpine AS build-env
LABEL maintainer "Jimmy Zelinskie <jimmyzelinskie+git@gmail.com>"

RUN apk add --no-cache curl git

WORKDIR /go/src/github.com/chihaya/chihaya
COPY . /go/src/github.com/chihaya/chihaya

RUN go mod tidy

RUN CGO_ENABLED=0 go install ./cmd/chihaya

FROM alpine:latest
RUN apk add --no-cache ca-certificates tcpdump
COPY --from=build-env /go/bin/chihaya /chihaya

ENTRYPOINT ["/chihaya"]
