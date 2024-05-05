FROM docker.io/library/golang:alpine AS build

ARG TARGETARCH

WORKDIR /src
RUN apk --no-cache add git ca-certificates \ &&
    git clone https://codeberg.org/librarian/librarian . \ &&
    go mod download \ && 
    GOOS=linux GOARCH=$TARGETARCH CGO_ENABLED=0 go build -ldflags "-X codeberg.org/librarian/librarian/pages.VersionInfo=$(date '+%Y-%m-%d')-$(git rev-list --abbrev-commit -1 HEAD)" -o /src/librarian

FROM scratch as bin

WORKDIR /librarian
COPY --from=build /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=build /src/librarian .

EXPOSE 3000
CMD ["/librarian/librarian"]
