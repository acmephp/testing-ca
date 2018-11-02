Acme Testing CA
===============

Provide a Certificate Authority server for testing purpose.

Requirements
------------

- docker

Usage
-----

Hosted on Docker Hub: https://hub.docker.com/r/acmephp/testing-ca/

Start the server container in background.

```bash
docker run -d --net host --add-host acmephp.com:127.0.0.1 acmephp/testing-ca
docker run -d --add-host acmephp.com:127.0.0.1 acmephp/testing-ca
```

> By design, to CA server will resolve the DNS for domains you are requesting.
> For testing purpose you have 2 way to resolve challenges
> * Running several containers in the same network. The domain to test is the
    name of the container. Docker will automatically resolve the name of the
    container
> * Starting `testing-ca` on the host network, and declare domains  with
    `--add-host`

```bash
docker run -d --net host --add-host acmephp.com:127.0.0.1 acmephp/testing-ca
docker run -d --add-host acmephp.com:127.0.0.1 acmephp/testing-ca
```

Configure your application to call the testing CA with the following endpoints

```
https://127.0.0.1:14000/dir
```
