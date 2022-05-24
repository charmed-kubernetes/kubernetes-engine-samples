FROM --platform=$TARGETPLATFORM golang:1.18-alpine
ARG TARGETPLATFORM
ARG TARGETOS
ARG TARGETARCH

WORKDIR /app
COPY main.go .
RUN echo "Building hello-app for ${TARGETPLATFORM}"
RUN GOOS=$TARGETOS GOARCH=$TARGETARCH go build -o hello-app main.go

FROM alpine:latest
COPY --from=0 /app/hello-app .
ENV PORT 8080
CMD ["./hello-app"]
