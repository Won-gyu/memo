By Schkn

In order to start a Bash shell in a Docker container, execute the “docker exec” command with the “-it” option and specify the container ID as well as the path to the bash shell.
```bash
$ docker exec -it <container> /bin/bash

# Use this if bash is part of your PATH

$ docker exec -it <container> bash
```

[source](https://devconnected.com/docker-exec-command-with-examples/)

To copy a file into a docker container.
```bash
docker cp script.sh jenkins:/tmp/script.sh
```