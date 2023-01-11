Build:
	hugo --destination ./dest
Clean:
	rm -rf ./dest
Post:
	hugo new posts/$(POST_NAME).md
	sed 's/title:/title: '$('POST_TITLE')' posts/$(POST_NAME).md