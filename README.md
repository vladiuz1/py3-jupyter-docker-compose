# py3-jupyter-docker-compose

This repo contains a easy-to configure jupyter notebook that runs from a `docker-compose`. Its useful when you have a
bunch of docker-compose services running, and you want to easily interact with their APIs via python jupyter-notebook.

##  Configure

1. Edit your .env so you can setup the password to access your notebook.

```yaml
token: sha1:
```