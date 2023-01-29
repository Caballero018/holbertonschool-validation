.PHONY: build

go-build:	## Builds the API binary file using go
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build /bin/bash -c "go mod init github.com/Caballero018/awesome-api && go get github.com/gorilla/mux && go build"

hugo-build:		## Builds a website using gohugo on the dist folder
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build hugo

build:	## Builds all that is needed for website
	-make go-build
	make hugo-build

post:		## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build hugo new posts/${POST_NAME}.md
	sed -i "s/title: .*/title: ${POST_TITLE}/" ./content/posts/${POST_NAME}.md

check:  ## Lints and check for dead links on markdowns using markdownlint-cli and markdown-link-check
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build markdownlint ./content/posts/*.md
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build markdown-link-check ./content/posts/*.md

validate: ## Validates dist/index.html using W3C Hbtn validator
	-make build
	-git clone https://github.com/holbertonschool/W3C-Validator.git
	-./W3C-Validator/w3c_validator.py ./dist/index.html
	-rm -rf ./W3C-Validator

run:	## Runs the built binary and send everything to awesome.log
	./awesome-api >./awesome.log 2>&1 &

stop:	## Terminates the execution of awesome-api
	kill $(shell pgrep awesome-api)

clean:	## Removes binary and logs
	-make stop
	-rm -rf awesome-api awesome.log coverage* go* awesome-website.zip ./dist

test:	## Tests API using go test
	-make build
	make unit-tests
	make integration-tests

lint:	## Lints all the go files using golangci-lint
	-make build-docker
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build markdownlint README.md DEPLOY.md
	docker run --rm --volume=$(shell pwd):/app --workdir=/app hadolint/hadolint hadolint build/Dockerfile

unit-tests:	## Runs implemented unit test using go test
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build go test -v -short -coverprofile=coverage-units.out

integration-tests:	## Runs integration test using go test
	docker run --rm --volume=$(shell pwd):/app --workdir=/app awesome:build go test -v -coverprofile=coverage-integrations.out

package:  ## Generates a zip archive to deployment
	-make build
	zip awesome-website.zip awesome-api dist/

build-docker:	## Builds a Docker image from Dockerfile on build directory
	docker build -t awesome:build ./build

docker-tests:	## Test the generated docker image using container-structure-test and cst.yml config file
	-make build-docker
	container-structure-test test --image awesome:build --config build/cst.yml

help:	## Show this help message
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//'
