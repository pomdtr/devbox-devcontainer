# Devbox Dev Container

Example integration between Devbox and VS Code Dev Containers.

## Adding a new dependency from the container

```sh
devbox --config /devbox/devbox.json add python310 && cp /devbox/devbox.json .devcontainer/devbox.json
```

Or use the `Add Package to Devbox` task.
