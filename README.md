# Title

## Setup
** Note that I have no clue if it works on windows, but it works on both mac and linux **
 - Install [docker](https://www.docker.com/community-edition).
 - Add the following code in your `~/.bash_profile`. If the file doesn't exist, create it.
```
devkitARM() { docker run --rm -it -u="$(id -g)" -v "$PWD":"/${PWD##*/}" -w "/${PWD##*/}" devkitpro/devkitarm "$@"; }
```

Once this is done, navigate to your nds project in terminal. You can then:
 - build with `devkitARM make`
 - clean with `devkitARM make clean`
