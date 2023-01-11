build:
	hugo --destination dist
clean:
	rm -rf ./dist
post:
	hugo new posts/$(POST_NAME).md
	sed -i '1s/.*//' posts/$(POST_NAME).md | echo 'title: '$('POST_TITLE')' >> posts/$(POST_NAME).md