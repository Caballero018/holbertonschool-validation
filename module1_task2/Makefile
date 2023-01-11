build:
	hugo --destination dist
clean: ## Cleanup the content of the directory dist/
	rm -rf ./dist
post:
	rm -rf content/posts/$(POST_NAME).md
	hugo new posts/$(POST_NAME).md
	sed -i 's/title*/title: "$(POST_TITLE)"/g' content/posts/$(POST_NAME).md
help:
	cat README.md
	