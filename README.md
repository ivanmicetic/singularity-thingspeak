# Singularity ThingSpeak
[ThingSpeak] server in a Singularity container.

## Prerequisites

The server needs MySQL database on host. Install and configure it with something like this:
```sh
sudo apt install mysql-server
mysql -e "CREATE USER 'thing'@'%' IDENTIFIED BY 'speak';"
mysql -e "GRANT ALL ON thingspeak_test.* TO 'thing'@'%';"
mysql -e "GRANT ALL ON thingspeak_development.* TO 'thing'@'%';"
mysql -e "GRANT ALL ON thingspeak_production.* TO 'thing'@'%';"
``` 

## Build

You can build a local Singularity image named `thingspeak.sif` with:

```sh
sudo singularity build thingspeak.sif thingspeak.def
```

## Run

You can run the server using the default run command:

```sh
singularity run thingspeak.sif
```
or as a Singularity instance

```sh
singularity instance start thingspeak.sif thingspeak
singularity instance list
singularity instance stop thingspeak
```

The server should be accessible at http://localhost:3000/.

You can override the listening port with an environment variable:

```sh
export SINGULARITYENV_LISTEN_PORT=3001
singularity run thingspeak.sif
```

## Contributing

Bug reports and pull requests are welcome on GitHub at
https://github.com/ivanmicetic/singularity-thingspeak.

## License

The code is available as open source under the terms of the [MIT License].

[ThingSpeak]: https://github.com/iobridge/thingspeak
[MIT License]: http://opensource.org/licenses/MIT
