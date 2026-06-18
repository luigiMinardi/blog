+++
title="How to use Docker on Mac Silicon"
description="How to use docker CLI on mac silicon without Docker Desktop."
summary="Setting up docker in mac without Docker Desktop nor headaches."
date="2026-02-04"
tags=["docker", "docker compose", "docker buildx", "mac", "colima"]
categories=["any", "tutorial", "programming", "devops"]
+++

This post teaches how to use docker on mac silicon without the need of Docker
Desktop.

## What is Docker
Docker is used as a container management so that your dev environment is closer
to prod and to other dev environments from your team.

[Docker Desktop](https://docs.docker.com/desktop/) is a GUI that provides
[Docker](https://github.com/docker/cli), [Docker Compose](https://github.com/docker/compose)
and [Docker Buildx](https://github.com/docker/buildx) (BuildKit).
It is the "recommended" way to download it in Windows and Mac.

> Just as a reminder, commercial use of Docker Desktop in larger enterprises
> (more than 250 employees or more than $10 million USD in annual revenue)
> requires a paid subscription.

## Installing on mac
if you want the "easy" and "recommended" path just use [Docker Desktop](https://docs.docker.com/desktop/setup/install/mac-install/)
preferably on the latest version.

But if you don't want to be forced into the paid subscription eventually you
need to do it "the hard way", dont worry, I will provide the easy path do have
it working just fine.

Install the cli with [homebrew](https://brew.sh)
```sh
brew install docker docker-compose docker-buildx
```

Run `docker info` to make sure the `Server` is working
```sh
docker info
```

### Fixing Docker on Mac Silicon
> This is only needed if you have a Mac with an arm chip (M1+ chip) and did not
> install Docker Desktop.

By running the brew install commands above if you then run `docker info` this
will show up:
```sh
$ docker info
Client: Docker Engine - Community
 Version:    XX.X.X
 Context:    default
 Debug Mode: false

Server:
failed to connect to the docker API at unix:///var/run/docker.sock; check if
the path is correct and if the daemon is running: dial unix
/var/run/docker.sock: connect: no such file or directory
```

The reason this happens is because docker was made for `x86` and Mac Silicon
is `arm`, the only official server for arm by Docker is through Docker Desktop
which is why they recommend it and how they make money.

Thus [Colima](https://github.com/abiosoft/colima) is needed to have a Linux VM
for containers using [Lima](https://github.com/lima-vm/lima) as your Server.

```sh
brew install colima
```
> this installs lima too as a dependency

then run
```sh
colima start
```
wait a little until it outputs that its done
```sh
INFO[0000] starting colima
INFO[0000] runtime: docker
INFO[0002] creating and starting ...                     context=vm
INFO[0137] provisioning ...                              context=docker
INFO[0139] starting ...                                  context=docker
INFO[0140] done
```

when the terminal is available again check `docker info`
```sh
docker info
```
now it should show
```sh
Client: Docker Engine - Community
 Version:    XX.X.X
 Context:    default
 Debug Mode: false

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.4.0
...
Name: colima
...
```

#### Remember to restart Colima after a `brew upgrade`:
> after restart, it takes a while to get up and running so don't panic if
> `docker info` do not show a Server for a few minutes
```sh
brew services restart colima
```

##### **My Colima is still broken, what do I do**
Check the [Colima Docker FAQ](https://github.com/abiosoft/colima/blob/main/docs/FAQ.md#docker)

#### Configuring Colima with Testcontainers
Colima uses Docker contexts to allow co-existence with other Docker servers and
sets itself as the default Docker context on startup. However, Testcontainers
is not aware of Docker contexts which leads to an error.

To fix it you need to configure Colima as the `DOCKER_HOST`.

##### *Zsh*
```sh
echo 'export DOCKER_HOST="unix://$HOME/.colima/default/docker.sock"' >> ~/.zshrc
```
```sh
source ~/.zshrc
```
##### *Bash*
```sh
echo 'export DOCKER_HOST="unix://$HOME/.colima/default/docker.sock"' >> ~/.bashrc
```
```sh
source ~/.bashrc
```

After setting the `DOCKER_HOST` to Colima, as a side effect the `docker.sock`
inside Testcontainers Ryuk is now pointing to `~/.colima/default/docker.sock`,
but inside the VM that path don't exist, so you need to tell Testcontainers to
use the default `docker.sock` path from inside the Ryuk VM.

##### *Zsh*
```sh
echo "export TESTCONTAINERS_DOCKER_SOCKET_OVERRIDE=/var/run/docker.sock" >> ~/.zshrc
```
```sh
source ~/.zshrc
```
##### *Bash*
```sh
echo "export TESTCONTAINERS_DOCKER_SOCKET_OVERRIDE=/var/run/docker.sock" >> ~/.bashrc
```
```sh
source ~/.bashrc
```

#### Configuring docker compose and Buildx
Add the necessary config for `docker compose` and `docker buildx` on
`~/.docker/config.json`

**DO NOT put `$HOMEBREW_PREFIX` there**, it needs to be the output of that
environment variable, run `echo $HOMEBREW_PREFIX` to see what is yours, if it
is `/opt/homebrew` then the path to put in the `cliPluginsExtraDirs` would be
`/opt/homebrew/lib/docker/cli-plugins`
```json
{
    "cliPluginsExtraDirs": [
     "$HOMEBREW_PREFIX/lib/docker/cli-plugins"
    ]
}
```
With a bare Colima config the config should look like this
```json
{
	"auths": {},
	"currentContext": "colima",
    "cliPluginsExtraDirs": [
     "/opt/homebrew/lib/docker/cli-plugins"
    ]
}
```
Then run `docker info`
```sh
$ docker info
Client: Docker Engine - Community
 Version:    29.2.1
 Context:    colima
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.31.1
    Path:     /opt/homebrew/lib/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  5.0.2
    Path:     /opt/homebrew/lib/docker/cli-plugins/docker-compose
```
check if both `Plugins` are listed if so it was a success.

## Installing on other OS's
In case you are not in mac you dont have all that hassle, I didn't want to make
multiple posts about it so I will just show how for them here too even if the
focus was mostly on how to fix Mac problems.
### Windows
[Docker Desktop](https://docs.docker.com/desktop/setup/install/windows-install/)
seem to be the way on windows, I recommend to use the WSL 2 backend.

You can install it through their website or with choco [Chocolatey](https://docs.chocolatey.org/en-us/choco/setup/#installing-chocolatey-cli)
```powershell
choco install docker-desktop
```
If you want to use docker on Windows without Docker Desktop you can probably do
through WSL2 and following the Linux install from there.

### Linux
[Docker Desktop](https://docs.docker.com/desktop/setup/install/linux/) latest.

Or install the cli only through your distro package manager (yes it's this easy)
##### Arch-based
```sh
pacman -S docker docker-compose docker-buildx
```
##### Debian-based
```sh
apt-get install -y docker docker-compose docker-buildx
```
##### Alpine
```sh
apk add --no-cache docker docker-cli-compose docker-cli-buildx
```

## How to use docker

Some useful commands in case something need to be done manually in the
containers I wont enter in detal on how to write a docker-compose or Dockerfile
here as this is usually written by a sysadmin/devops and not a dev.

If you have your `docker-compose.yml` inside a directory (so not in your project
ROOT) every `docker` command will need to have the `f` flag following the
directory where the yml file is at.

So for a `dir` directory at your ROOT you need to add `-f dir/docker-compose.yml`
before the docker command

Examples
```sh
docker compose -f dir/docker-compose.yml <command>
```
to remove the containers then you can do
```sh
docker compose -f dir/docker-compose.yml down --volumes --remove-orphans
```
If you are inside `dir` (or docker-compose.yml) is on your ROOT you will always
run
```sh
docker compose <command>
```
To make migrations of a django project with a docker-compose `services` called
`web` using `uv` you would run
```sh
docker compose web uv run manage.py makemigrations
```

### Enter the container
> To run only one command you can just replace the `bash` with the command you
> want to run instead, that way the command is run instead of entering in a
> shell.
```sh
docker compose exec web bash
```
after running the above command it's possible to for example see all applied
migrations on a django project
```sh
uv run manage.py showmigrations
```
after finishing
#### leave the container
```sh
exit
```

### Removing the container

To remove the containers to rebuild the docker images and services do
```sh
docker compose down --volumes --remove-orphans
```

### Linting a Dockerfile
[Hadolint](https://github.com/hadolint/hadolint) is a tool that can be used to
lint the Dockerfile by running
```sh
hadolint dir/Dockerfile
```
or if you have your Dockerfile on ROOT or is inside `dir`
```sh
hadolint Dockerfile
```
