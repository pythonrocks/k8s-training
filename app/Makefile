VERSION ?= 0.2

.PHONY: build
build:
	docker build -t my-api .

.PHONY: tag
tag:
	docker tag my-api:latest eu.gcr.io/long-ratio-272315/my-api:$(VERSION)

.PHONY: push
push:
	docker push eu.gcr.io/long-ratio-272315/my-api:$(VERSION)
