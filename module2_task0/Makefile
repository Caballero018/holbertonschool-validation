build:	## Builds the API binary file using go
	go build

run:	## Runs the built binary and send everything to awesome.log
	./awesome-api >./awesome.log 2>&1 &

stop:	## Terminates the execution of awesome-api
	kill $(shell pgrep awesome-api)

clean:	## Removes binary and logs
	make stop
	rm ./awesome-api awesome.log

test:	## Tests the API using curl
	curl http://localhost:9999 
	curl http://localhost:9999/health 

help:	## Show this help message
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//'
