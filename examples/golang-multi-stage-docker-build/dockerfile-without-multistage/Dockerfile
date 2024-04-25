###########################################
# BASE IMAGE
###########################################

FROM ubuntu AS build

# Install Go
RUN apt-get update && apt-get install -y golang-go

# Set environment variable for Go modules
ENV GO111MODULE=off

# Copy project files into the image
COPY . .

# Build the Go application
RUN CGO_ENABLED=0 go build -o /app .

# Set the entry point for the container
ENTRYPOINT ["/app"]

