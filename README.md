[![service status](https://img.shields.io/static/v1?label=service&message=status&color=blue)](https://status.steamcmd.net)
[![StackShare](http://img.shields.io/badge/tech-stack-blue.svg?style=flat)](https://stackshare.io/jona/steamcmd-web)

# SteamCMD Web

Statically generated website and docs for the SteamCMD API based on [Hugo](https://gohugo.io/)

### Configuration

Two different configs are used. One for development and one during production. You can find them in the config directory:
```
config/
  development/
    config.toml
  production/
    config.toml
```
When the local Hugo webserver is used during development (with the `serve` command), the `development` config is automatically used.
Otherwise when a full build is done via Hugo, the `production` config is automatically used.

### Development Docker

The easier way to setup a local development environment for testing changes is using Docker Compose.
You can spin up the Hugo Builder container and CORS container with the `docker-compose` command:
```
docker-compose up
```
After executing this command you should be able to reach the URL on [http://localhost:1313/](http://localhost:1313/).

### Development Manual

As an alternative for using Docker Compose you can spin up a local webserver and generate on-the-fly with the following Hugo command.
By default the webserver is only reachable on localhost (127.0.0.1) and you will need to add the bind parameter to make it reachable.
```
hugo serve -D
hugo serve -D --bind="0.0.0.0"
```
To avoid CORS error with the API's used in Javascript you can use a/the Local CORS Proxy. Install this with:
```
sudo npm install -g local-cors-proxy
```
And run it locally with:
```
lcp --proxyUrl https://api.steamcmd.net --port 3000
lcp --proxyUrl https://api.steampowered.com --port 3001
```
