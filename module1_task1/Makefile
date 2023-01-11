build:
	hugo --destination ./dest
clean:
	rm -rf ./dest
post:
	hugo new posts/$(POST_NAME).md
	sed 's/title:/title: '$('POST_TITLE')' posts/$(POST_NAME).md