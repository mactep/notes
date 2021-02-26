# This is an example to cross build to arm. If using pip check
[this](202101262104_pip_arm.md)

```
docker run --privileged --rm tonistiigi/binfmt --install arm
docker run -d -p 5000:5000 --name registry registry:2
docker buildx build -t localhost:5000/NAME:TAG --platform linux/arm/v7 --push .
```
The first command adds platform support. Then we start a local registry and
build the image, pushing it to the registry.

#docker
#arm
