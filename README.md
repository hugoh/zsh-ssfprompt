# zsh-ssfprompt: slim, simple, fast prompt for Zsh

This is prompt for zsh designed to be:
- Simple: only shows the information that matters
- Slim: fits on one line, with VCS information on the right and disappearing as needed
- Fast: expensive lookups are minimized and done asynchronously

It's likely going to evolve very little (if at all) functionality-wise.

## Install

I recommend a zsh plugin manager, such as zplug:

```sh
zplug 'hugoh/zsh-ssfprompt', use:'prompt_*', from:gitlab, lazy:true
```

Then, activate with:

```sh
autoload -U promptinit && promptinit
prompt ssfprompt
```

## Requirements

For asynchronous lookups, you will need to install [zsh-async](https://github.com/mafredri/zsh-async).

Again, with zplug:

```sh
zplug 'mafredri/zsh-async', if:'is-at-least 4.3.11 >& /dev/null'
```

## Customization

There are limited customization options via `zstyle`. Check `prompt_ssfprompt_setup()` for available options.
