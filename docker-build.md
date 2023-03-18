# Build and Push Docker Image Action
This GitHub Action builds a Docker image from a Dockerfile and pushes it to a Docker registry.


```
  uses: your-org/build-and-push-docker-image@v1.0.0
  with:
    image-name: my-docker-image:v1.0.0
    registry-url: docker.pkg.github.com
    registry-username: ${{ secrets.DOCKER_REGISTRY_USERNAME }}
    registry-password: ${{ secrets.DOCKER_REGISTRY_PASSWORD }}
    build-args: |
      --build-arg FOO=bar
      --build-arg BAZ=qux
```

This example builds a Docker image from the Dockerfile in the root of the repository, gives it the name my-docker-image:v1.0.0, and pushes it to the Docker registry at docker.pkg.github.com. The build-args input is also used to pass two build arguments to the Docker build command.

You can also specify a custom path to the Dockerfile using the dockerfile-path input:

```
  uses: your-org/build-and-push-docker-image@v1.0.0
  with:
    dockerfile-path: path/to/Dockerfile
    image-name: my-docker-image:v1.0.0
    registry-url: docker.pkg.github.com
    registry-username: ${{ secrets.DOCKER_REGISTRY_USERNAME }}
    registry-password: ${{ secrets.DOCKER_REGISTRY_PASSWORD }}
```
In this example, the Dockerfile is located at path/to/Dockerfile instead of the default location at the root of the repository.
