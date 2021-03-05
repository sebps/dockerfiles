# Use the offical golang image to create a binary.
# This is based on Debian and sets the GOPATH to /go.
# https://hub.docker.com/_/golang
FROM golang:1.15-buster as builder

# Create and change to the app directory.
WORKDIR /apps

# Retrieve the last version of the redirect module
RUN GOBIN=/apps NOGOPROXY=github.com/sebpsdev go get github.com/sebpsdev/golibs/redirect

RUN ls /apps

# Use the official Debian slim image for a lean production container.
# https://hub.docker.com/_/debian
# https://docs.docker.com/develop/develop-images/multistage-build/#use-multi-stage-builds
FROM debian:buster-slim

# Copy the binary to the production image from the builder stage.
COPY --from=builder /apps/redirect /apps/redirect

# Run the redirect server on container startup
ENTRYPOINT ["/apps/redirect"]

# Specify default arguments for the redirection
CMD ["--sourcePort=80", "--targetPort=5000", "--targetHost=host.docker.internal"]