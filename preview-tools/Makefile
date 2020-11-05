IMAGE_NAME := workshop
OCI_FNAME := Containerfile
#SERVER_NAME := core.example.com:5000

help:
	@echo "make container-build - Build and locally tag a new OCI image."
	@echo "make container-build-force - Use a no-cache build"
	@echo "make container-run - Run container detached"
	@echo "make container-run-i - Run container interactive"

container-build:
	@podman build --file=$(OCI_FNAME) -t $(IMAGE_NAME) ../

container-build-force:
	@podman pull fedora-minimal:29
	@podman build --file=$(OCI_FNAME) -t $(IMAGE_NAME) --no-cache ../

container-run:
	podman run -d -v ${PWD}/..:/opt/workshop -P --name workshop $(IMAGE_NAME)

container-run-i:
	podman run --rm -v ${PWD}/..:/opt/workshop -it -P --name workshop --entrypoint "/bin/bash" $(IMAGE_NAME)

# push: tag
# 	@podman push $(SERVER_NAME)/$(IMAGE_NAME)

# pull:
# 	@podman pull $(SERVER_NAME)/$(IMAGE_NAME)
# 	@podman tag $(SERVER_NAME)/$(IMAGE_NAME) $(IMAGE_NAME)

# tag:
# 	@podman tag localhost/$(IMAGE_NAME) $(SERVER_NAME)/$(IMAGE_NAME)
