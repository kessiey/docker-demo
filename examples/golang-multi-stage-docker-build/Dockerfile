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

############################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD
############################################

FROM scratch

# Copy the compiled binary from the build stage
COPY --from=build /app /app

# Set the entrypoint for the container to run the binary
ENTRYPOINT ["/app"]

