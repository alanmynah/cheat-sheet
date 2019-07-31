Note `.travis.yml` was originally located in the root folder. This is why all the paths are from there

This is not the ideal approach, but good to get started with.

An example to show how to work with:

- Individual containers per environment:
  - dev container `dev.Dockerfile` - it is not `.dev` for intellisense reasons.
  - ci container - it's the same as `dev.Dockerfile`, but has CI=true env variable set.
  - prod container `Dockerfile` that uses multistep build to serve the app with nginx
- TravisCI, [the config is here](../../dev-prod-container.travis.yml)
- Elastic beanstalk

Dev docker

```sh
docker-compose run --build
```

Prod docker

```sh
docker build . # Сopy <image-id>
# Default nginx port is 80
docker run -p 8080:80 <image-id>
```
