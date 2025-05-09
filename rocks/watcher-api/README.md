# watcher-api ROCK

This is a ROCK OCI image for watcher-api.

More information is coming.

For now, if you want to play with it:

```bash
> sudo snap install rockcraft --edge --classic
> rockcraft pack
```

Now that you have created the ROCK, you can import it into
your local docker repository. Using skopeo is a good idea as
it will help ensure that all layers of the image are imported
into docker (this is just the top layer).

```bash
> skopeo --insecure-policy copy oci-archive:watcher-api_2025.1_amd64.rock docker-daemon:watcher-api:2025.1
```

If you are interested in giving it a go in Microk8s, you can
export the image from your docker registry and then into the
microk8s registry:

```bash
> docker save watcher-api:2025.1 > ./watcher-api_2025.1.tar
> microk8s ctr image import ./watcher-api_2025.1.tar
# Try with sunbeam
> juju attach-resource watcher-k8s watcher-api-image=watcher-api:2025.1
```
