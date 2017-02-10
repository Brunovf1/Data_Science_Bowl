help:
	@cat Makefile

DATA?="${HOME}/Data"
DOCKER_FILE=Dockerfile
DOCKER=docker
BACKEND=tensorflow
TEST=tests/
SRC?=$(shell dirname `pwd`)
IMG?=keras

build:
	docker build -t $(IMG) --build-arg python_version=3.5 -f $(DOCKER_FILE) .

bash: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) bash

ipython: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) ipython

notebook: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --net=host --env KERAS_BACKEND=$(BACKEND) $(IMG)

test: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) py.test $(TEST)