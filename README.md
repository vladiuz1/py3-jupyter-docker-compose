# py3-jupyter-docker-compose

This repo contains a easy-to configure jupyter notebook that runs from a `docker-compose`. Its useful when you have a
bunch of docker-compose services running, and you want to easily interact with their APIs via python jupyter-notebook.


## Run

All you need to do is use the regulare docker-compose command:

```
docker-compose up -d
```

## Stop

```
docker-compose down

```

## Access

This is the default location of the notebook:

```
http://127.0.0.1:8888/
```

The defualt password is `changeme`

In order to make the container publicly available, edit `docker-compose.yaml` and replace `- "127.0.0.1:8888:8888"` 
with `- "8888:8888"`. Remember, changing the port and host inside `jupyter-config.json` will only change the settings
inside the container, and likely to break the notebook.

##  Configure

The config files are located in `./config` folder, edit the `jupyter-config.json` for customization.

Remember that the local `./config` dir is mounted as `/home/jovyan/.jupyter/config` within the container.

### Passphrase

The default passphrase to access the notebook is `changeme`.

You will need to edit the `./config/jupyter-config.json` file and change the value of `NotebookApp.password` key. The
passphrase can be generated using the following command:

```yaml
./passphrase
```

Use the output of the command to set the `NotebookApp.password` key.

### ssl

If you choose to set ssl certificates, place them in the `./config` folder and state the location of the files
as absolute paths in `./config/jupyter-config.json` starting with `/home/jovyan/work`:

```json
{
  "NotebookApp": {

    "certfile": "/home/jovyan/.jupyter/config/ssl-cert.pem",
    "keyfile": "/home/jovyan/.jupyter/config/ssl-cert.key",

  }
}
```