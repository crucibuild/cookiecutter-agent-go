default: check

.PHONY: check ci dependencies

dependencies:
	go get -t -v ./...
	go get -v "github.com/omeid/go-resources/cmd/resources"

check: dependencies
	go get -u github.com/alecthomas/gometalinter
	gometalinter --install --update
	gometalinter -j2 --config "$(CURDIR)/gometalinter.json" ./...

build: dependencies
	resources -output="resources.go" -var="Resources" -trim="" resources/* schema/*
	go build ./...

ci: build #TODO fix warnings check
	true
