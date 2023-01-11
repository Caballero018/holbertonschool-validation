build:	## Generate the website from the markdown and configuration files in the directory dist/.
	hugo --destination dist
clean:	## Cleanup the content of the directory dist/
	rm -rf ./dist
post:	## Create a new blog post whose filename and title come from the environment variables POST_TITLE and POST_NAME.
	rm -rf content/posts/$(POST_NAME).md
	hugo new posts/$(POST_NAME).md
	sed -i 's/title*/title: "$(POST_TITLE)"/g' content/posts/$(POST_NAME).md

# Add the following 'help' target to your Makefile
# And add help text after each target name starting with '\#\#'
 
help:           ## Show this help.
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//'
 
# Everything below is an example
 
target00:       ## This message will show up when typing 'make help'
	@echo does nothing
 
target01:       ## This message will also show up when typing 'make help'
	@echo does something
 
# Remember that targets can have multiple entries (if your target specifications are very long, etc.)
target02:       ## This message will show up too!!!
target02: target00 target01
	@echo does even more