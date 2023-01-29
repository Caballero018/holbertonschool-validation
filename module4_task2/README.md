# My Awesome API

## Prerequisites

go and make installed

## Lifecycle

go-build:        Builds the API binary file using go
hugo-build:              Builds a website using gohugo on the dist folder
build:   Builds all that is needed for website
post: Create a new blog post whose filename and title come from the environment
variables POST_TITLE and POST_NAME
check:   Lints and check for dead links on markdowns using markdownlint-cli and
markdown-link-check
validate:  Validates dist/index.html using W3C Hbtn validator
run:     Runs the built binary and send everything to awesome.log
stop:    Terminates the execution of awesome-api
clean:   Removes binary and logs
test:    Tests API using go test
lint:    Lints all the go files using golangci-lint
unit-tests:      Runs implemented unit test using go test
integration-tests:       Runs integration test using go test
package:   Generates a zip archive to deployment
build-docker:    Builds a Docker image from Dockerfile on build directory
docker-tests: Test the generated docker image using container-structure-test
and cst.yml config file
help:    Show this help message

## Workflow

Github actions has been activated. Workflows can be found at directory
.github/workflows
