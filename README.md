# zsh-ssfprompt: slim, simple, fast prompt for Zsh

This is prompt for zsh designed to be:
- Simple: only shows the information that matters
- Slim: fits on one line, with VCS information on the right and disappearing as needed
- Fast: expensive lookups are minimized and done asynchronously

It's likely going to evolve very little (if at all) functionality-wise.

![Screenshot](https://gitlab.com/hugoh/zsh-ssfprompt/uploads/e82849c541f86ac0366b202030ccab90/screenshot-zsh-ssfprompt.png)

## Install

I recommend a zsh plugin manager, such as antigen:

```sh
antigen bundle https://gitlab.com/hugoh/zsh-ssfprompt
```

## Requirements

For asynchronous lookups, you will need to install [zsh-async](https://github.com/mafredri/zsh-async).

Again, with antigen:

```sh
antigen bundle mafredri/zsh-async
antigen bundle https://gitlab.com/hugoh/zsh-ssfprompt
```

## Customization

There are limited customization options via `zstyle`. Check `prompt_ssfprompt_setup()` for available options.
