help:
	@cat Makefile

DATA?="${HOME}/data"
DOCKER_FILE=Dockerfile
DOCKER=docker
BACKEND=tensorflow
TEST=tests/
SRC?=$(shell dirname `pwd`)
IMG?=brunovf1/keras-tf

build:
	docker build -t $(IMG)  -f $(DOCKER_FILE) .

bash: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) bash

ipython: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) ipython

notebook: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --net=host --env KERAS_BACKEND=$(BACKEND) $(IMG)

test: build
	$(DOCKER) run -it -v $(SRC):/src -v $(DATA):/data --env KERAS_BACKEND=$(BACKEND) $(IMG) py.test $(TEST)
