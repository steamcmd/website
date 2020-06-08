[![CodeFactor](https://www.codefactor.io/repository/github/steamcmd/website/badge/master)](https://www.codefactor.io/repository/github/steamcmd/website/overview/master)
[![Service Status](https://img.shields.io/static/v1?label=service&message=status&color=blue)](https://status.steamcmd.net/782831276)
[![StackShare](http://img.shields.io/badge/tech-stack-blue.svg?style=flat)](https://stackshare.io/jona/steamcmd-web)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# SteamCMD Web

Statically generated website and docs for the SteamCMD API build with [Jekyll](https://jekyllrb.com).

## Development

For local development you can use Jekyll on the command line and run the build-in development server locally. The easiest way however is using Docker Compose. This is a quick way to spin up the Jekyll development environment and a CORS container to fix CORS issues with client-side API calls.

### Docker Method

You will only need to have Docker installed. Run the Docker Compose command to start the containers:
```shell
docker-compose up
```
After executing this command you should be able to reach the URL on [http://localhost:4000/](http://localhost:4000/).

### Manual Method

Install [Jekyll](https://jekyllrb.com) and it's prerequisites if you don't have them installed yet:
```shell
gem install bundler jekyll github-pages
bundle install
```
By default the build-in webserver is only reachable on localhost (127.0.0.1) and you will need to add the bind parameter to make it reachable.
```shell
bundle exec jekyll serve --config _config-dev.yml
bundle exec jekyll serve --config _config-dev.yml --host 0.0.0.0
```
To avoid CORS error with the API's used in Javascript you can use a/the Local CORS Proxy. Install this with:
```shell
sudo npm install -g local-cors-proxy
```
And run it locally with:
```shell
lcp --proxyUrl https://api.steamcmd.net --port 3000
lcp --proxyUrl https://api.steampowered.com --port 3001
```

## Configuration

Two different configs are used. One for development and one for the production build. You can find them in the root directory:

*   `_config.yml`
*   `_config-dev.yml`

By default the `_config.yml` config is used. During development it's recommend to specify the development `_config-dev.yml` config. The Docker Compose file specifies the development config as well.
