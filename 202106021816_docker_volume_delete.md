# Docker volume
If you delete the folder which is being pointed by docker volume, it'll not
detect that directory if you create it again.

For example, if you serve a site with nginx docker image and point to the
dist/something, `ng build` will delete that directory and create again. Move it
somewhere else so you can deploy it continuously.

#angular
#docker
#nginx
