# My Awesome API

## Prerequisites
go and make installed

## Lifecycle
go-build: Builds the API binary.
hugo-build: Builds a website.
build:   Website.
post: Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME
check:   Lints and check for dead links on markdowns using markdownlint-cli and markdown-link-check
validate:  Validates dist/index.html using W3C Hbtn validator
run:     Runs the built binary and send everything to awesome.log
stop:    Terminates the execution of awesome-api
clean:   Removes binary and logs
test:    Tests API using go test
lint:    Lints all the go files using golangci-lint
unit-tests:      Runs implemented unit test using go test
integration-tests:       Runs integration test using go test
help:    Show this help message
