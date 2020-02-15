# docker_buildx

GitHub Action to build and publish images using [Docker Buildx](https://docs.docker.com/buildx/working-with-buildx/).

## Inputs
The accepted inputs are:

| Name          | Type      | Default   | Mandatory   |  Description                                                    |
|---------------|-----------|-----------|-------------|-----------------------------------------------------------------|
| `tag`         | String    | `latest`  | No          | Tags (*comma separated*) to apply to the image                  |
| `imageName`   | String    |   | Yes         | Name of the image                                               |
| `dockerFile`  | String    | `Dockerfile` | No       | Name of the Dockerfile |
| `buildArg`    | String    | `none`       | No       | Docker build `--build-arg` flags (*comma separated*) |
| `publish`     | Boolean   | `false`   | No          | Indicate if the builded image should be published on Docker HUB |
| `platform`    | String    | `linux/amd64,linux/arm64,linux/arm/v7`  | No         | Platforms (*comma separated*) that should be used to build the image |                 |
| `dockerHubUser`   | String    |   | Only if `publish` is true         | User that will publish the image                 |
| `dockerHubPassword`   | String    |   | Only if `publish` is true         | Password of the `dockerHubUser`                 |

## Example of usage

```
jobs:
    build:
        runs-on: ubuntu-latest
        name: Build image job
        steps:
            - name: Checkout master
              uses: actions/checkout@master
            - name: Build and publish image
              uses: ilteoood/docker_buildx@master
              with:
                publish: true
                imageName: YOUR_IMAGE_NAME_HERE
                dockerHubUser: YOUR_USER_HERE
                dockerHubPassword: YOUR_PASSWORD_HERE
```
