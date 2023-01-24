build:	## Generate the website from the markdown and configuration files in the directory dist/.
	hugo --destination dist
clean:	## Cleanup the content of the directory dist/
	rm -rf ./dist
post:	## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME.
	rm -rf content/posts/$(POST_NAME).md
	hugo new posts/$(POST_NAME).md
	sed -i 's/title*/title: "$(POST_TITLE)"/g' content/posts/$(POST_NAME).md
help:	## Print instructions for create a web site.
	cat README.md
package: ## Target named package which produces a file awesome-website.zip
	@hugo
	@sudo zip awesome-website.zip awesome-api dist/ 
lint: ## The target lint should be updated to lint the files README.md and DEPLOY.md with markdownlint
	markdownlint "*.md"
unit-tests: ## unit tests
	@echo "all tests done"

integration-tests: ## integration-tests
	@echo "all integration-tests done"

validate: ## validate
	@echo "all validations done"