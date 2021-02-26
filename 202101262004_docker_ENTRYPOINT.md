# What is the ENTRYPOINT instruction in docker

It's a stubborn version of CMD.

ENTRYPOINT has two forms:
- ENTRYPOINT ["executable", "param1", "param2"], can use CMD or input commands
  to add parameters;
- ENTRYPOINT command param1 param2, just overrides CMD and input commands

[reference article](https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/)

#docker
