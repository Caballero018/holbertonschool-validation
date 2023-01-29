.PHONY: build
IMAGE_TAG=$(shell git tag | tail -n 1)
ifeq ($(strip $(IMAGE_TAG)),)
IMAGE_TAG=$(shell git rev-parse --abbrev-ref HEAD)
endif

go-build:	## Builds the API binary file using go
	go mod init github.com/Caballero018/awesome-api && go get github.com/gorilla/mux && go build

hugo-build:		## Builds a website using gohugo on the dist folder
	hugo

build: 	## Builds all that is needed for website
	-make go-build
	make hugo-build

post:		## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME
	hugo new posts/${POST_NAME}.md
	sed -i "s/title: .*/title: ${POST_TITLE}/" ./content/posts/${POST_NAME}.md

check:  ## Lints and check for dead links on markdowns using markdownlint-cli and markdown-link-check
	markdownlint ./content/posts/*.md
	markdown-link-check ./content/posts/*.md

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
	markdownlint README.md DEPLOY.md
	wget -O hadolint https://github.com/hadolint/hadolint/releases/download/v2.12.0/hadolint-Linux-x86_64
	chmod u+x ./hadolint
	./hadolint Dockerfile

unit-tests:	## Runs implemented unit test using go test
	go test -v -short -coverprofile=coverage-units.out

integration-tests:	## Runs integration test using go test
	go test -v -coverprofile=coverage-integrations.out

package:  ## Generates a zip archive and a docker image to deployment
	docker build -t awesome:${IMAGE_TAG} .
	docker save -o awesome_image.tar awesome:${IMAGE_TAG}
	zip awesome-website.zip awesome-api dist/ awesome_image.tar

docker-tests:	## Test the generated docker image using container-structure-test and cst.yml config file
	container-structure-test test --image awesome:${IMAGE_TAG} --config cst.yml

help:	## Show this help message
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//'
