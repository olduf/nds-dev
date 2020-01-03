# Installing DevkitARM
## Through the DevkitPRO website
You can get the instruction on how to install DevkitARM on the official [website](https://devkitpro.org/wiki/Getting_Started).

## Through Docker
Going the docker way has the advantage of being easier and faster to install, but because the `libnds`/`devkitARM` files are in a docker image, you will probably have trouble setting up the includes and paths in your IDE. It's probably doable by exposing them as a volume, but I did not try it, so you're on your own for that.

Use this if you really don't want to install the library on your computer.

### Install Docker
You can install docker community edition through the official [website](https://www.docker.com/community-edition).

#### Setting up a shortcut command
**Note that I have no clue if it works on windows, but it works on both mac and linux**

Add the following code in your `~/.bash_profile`. If the file doesn't exist, create it.
```
devkitARM() { docker run --rm -it -u="$(id -g)" -v "$PWD":"/${PWD##*/}" -w "/${PWD##*/}" devkitpro/devkitarm "$@"; }
```

#### What it does
 - `--rm`: Cleanup the container after the command finishes.
 - `-it`: Allocate a tty for the container process.
 - `-u="$(id -g)"`: Set the docker user as the effective group ID instead of root.
 - `-v "$PWD":"/${PWD##*/}"`: Link the current directory as a volume.
 - `-w "/${PWD##*/}"`: Set the current directory as the docker working directory.

#### What it does

### Using the shortcut command

Once this is done, either source the file (`. ~/.bash_profile`) or start a new terminal session. Navigate to your nds project in terminal. You can then:
 - build with `devkitARM make`
 - clean with `devkitARM make clean`
