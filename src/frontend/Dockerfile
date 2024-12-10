FROM golang:1.22.2 as builder
WORKDIR /src

COPY go.mod go.sum ./
RUN go mod download
COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -o /go/bin/frontend .

FROM scratch

WORKDIR /src
COPY --from=builder /go/bin/frontend /src/frontend
COPY ./templates ./templates
COPY ./static ./static
ARG PORT=8080
ENV APP_PORT=$PORT

EXPOSE $PORT
ENTRYPOINT ["/src/frontend"]