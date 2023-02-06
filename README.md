# Running Jenkins in Docker

This project will create a custom jenkins controller image and execute it along with a docker sidecar container. The controller will be configured using the configuration-as-code Jenkins plugin.

## Build the jenkins controller image

``` sh
export JENKINS_ADMIN_ID="admin"
export JENKINS_ADMIN_PASSWORD="admin"
docker compose build
```
## Run the stack

``` sh
docker compose up -d
docker compose logs -f
```
## Tear down

``` sh
docker compose down -v
```
