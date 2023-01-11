build:
	hugo --destination dist
clean:
	rm -rf ./dist
post:
	rm -rf content/posts/$(POST_NAME).md
	hugo new posts/$(POST_NAME).md
	sed -i '1s/.*//' content/posts/$(POST_NAME).md | echo 'title: '$('POST_TITLE')' >> content/posts/$(POST_NAME).md