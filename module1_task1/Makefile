build:
	hugo --destination dist
clean:
	rm -rf ./dest
post:
	hugo new posts/$(POST_NAME).md
	sed -i '1s/.*/title: '$('POST_TITLE')'/' file.txt