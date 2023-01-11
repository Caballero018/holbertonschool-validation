build:	## Generate the website from the markdown and configuration files in the directory dist/.
		hugo --destination ./dist

clean:	## Cleanup the content of the directory dist/
		rm -r ./dist

post:	## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME.
		@rm -rf content/posts/$(POST_NAME).md
		hugo new posts/$(POST_NAME).md
		sed -i 's+title*.title: "$(POST_TITLE)"+g' content/posts/$(POST_NAME).md

help:	## Print Readme file of current directory.
		cat README.md
