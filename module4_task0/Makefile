go-build:
	docker run -d golang:1.15.8-buster go mod init github.com/Caballero018/awesome-api
	docker run -d golang:1.15.8-buster go get github.com/gorilla/mux
	docker run -d golang:1.15.8-buster go build

hugo-build:	## Generate the website from the markdown and configuration files in the directory dist/.
	hugo --destination dist
build:
	-make go-build
	make hugo-build
clean:	## Cleanup the content of the directory dist/
	rm -rf ./dist
post:	## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME.
	rm -rf content/posts/$(POST_NAME).md
	hugo new posts/$(POST_NAME).md
	sed -i 's/title*/title: "$(POST_TITLE)"/g' content/posts/$(POST_NAME).md
help:	## Print instructions for create a web site.
	cat README.md
package: ## Target named package which produces a file awesome-website.zip
	-make build
	zip awesome-website.zip awesome-api dist/ 
lint: ## The target lint should be updated to lint the files README.md and DEPLOY.md with markdownlint
	markdownlint "*.md"
unit-tests: ## unit tests
	@echo "all tests done"

integration-tests: ## integration-tests
	@echo "all integration-tests done"

validate: ## validate
	@echo "all validations done"