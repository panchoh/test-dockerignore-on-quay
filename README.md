# Test .dockerignore ignoring Dockerfile on Quay.io

## Suspected bug
When a `.dockerignore` is used that ignores `Dockerfile`, quay.io refuses to build the image,
complaining that the Dockerfile cannot be found.  This is, IMHO, unexpected behaviour,
since the [official docs](https://docs.docker.com/engine/reference/builder/#/dockerignore-file)
clearly state that:

> You can even use the `.dockerignore` file to exclude the `Dockerfile` and
> `.dockerignore` files. These files are still sent to the daemon because it
> needs them to do its job. But the `ADD` and `COPY` commands do not copy them
> to the image.

Also note that building this image works flawlessly both locally, with
```shell
$ docker build --tag pancho/test-dockerignore-on-quay:locally-built .
```
and
on
[hub.docker.com](https://hub.docker.com/r/pancho/test-dockerignore-on-quay/builds/),
but fails
on
[quay.io](https://quay.io/repository/pancho/test-dockerignore-on-quay?tab=builds).

Thanks for watching.

# UPDATE 20200404
I've checked and this now works OK on Quay.io.
Archiving...
