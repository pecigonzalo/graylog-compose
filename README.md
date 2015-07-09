# Graylog2 in docker-compose
This `docker-compose.yml` runs all the required processes for a Graylog setup on multiple docker containers.

The following processes are run in their own docker containers

* mongodb
* elasticsearch
* graylog

## Setup
This setup assumes you already have docker-compose and docker installed.

```
git clone git@github.com:pecigonzalo/graylog-compose.git
cd graylog-compose
docker-compose build
docker-compose up
```

## Play
Open [https://localhost:9443/](https://localhost:9443/) and use the login. (It may take a minute for the graylog server to come online)

```
username: admin
password: password
```

Then go to the [Content Packs](https://localhost:9443/system/contentpacks) page, upload the provided content pack, and then click "Apply content".

### Input
You can now go to the [Inputs page](https://localhost:9443/system/inputs) and see that the Docker GELF input has been entered to consume [logspout](https://github.com/gliderlabs/logspout) mesages from Docker (using the [GELF module](https://github.com/micahhausler/logspout-gelf)).

### Streams
Go to the [Streams page](https://localhost:9443/streams#) to see the example streams that have been created. Clock on each one to see past messages.

_[Hint: Open an incognito window and enter an invalid password in the Graylog login page. This will generate some content for you to see in your streams and dashboard.]_

### Dashboards
Go to the [Dashboards page](https://localhost:9443/dashboards) to see an example dashboard with graphs based on the 2 preconfigured streams.

### Plugins
Go to the [Graylog Plugin page](https://marketplace.graylog.org/) to see available plugins. Simply drop them in the `plugin/` directory in the project, and they'll be loaded when you restart Graylog.

### API explorer
Go to the Graylog API-Explorer [http://localhost:12900/api-browser](http://localhost:12900/api-browser) From here, you can play around with their [swagger](http://swagger.io/) api explorer.


## License
MIT License
