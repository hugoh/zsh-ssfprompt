# zsh-ssfprompt: slim, simple, fast prompt for Zsh

This is prompt for zsh designed to be:
- Simple: only shows the information that matters
- Slim: fits on one line, with VCS information on the right and disappearing as needed
- Fast: expensive lookups are minimized and done asynchronously
- Simple implementation: heavily relies on existing libraries

It's likely going to evolve very little (if at all) functionality-wise.

[![asciicast](https://asciinema.org/a/286672.png)](https://asciinema.org/a/286672)

## Install

I recommend a zsh plugin manager, such as [Zplugin](https://github.com/zdharma/zplugin):

```sh
zplugin light https://gitlab.com/hugoh/zsh-ssfprompt.git
```

## Requirements

* For asynchronous lookups, you will need to install [zsh-async](https://github.com/mafredri/zsh-async).
* One Git status module; by default, it uses [posh-git-sh](https://github.com/lyze/posh-git-sh)

Again, with Zplugin:

```sh
zplugin light mafredri/zsh-async
zplugin ice pick'git-prompt.sh'; zplugin light lyze/posh-git-sh
zplugin light https://gitlab.com/hugoh/zsh-ssfprompt.git
```

## Customization

You can of course defined your own `PROMPT` variable.

You can also override the Git status function to your liking.

To use [Starship](https://starship.rs/), configure the Git information to be in the right prompt and then:

```sh
prompt_ssfprompt_vcs_status() { command starship prompt --right }
```

To use [gitHUD](https://github.com/gbataille/gitHUD):

```sh
prompt_ssfprompt_vcs_status() { command githud zsh }
```

To use [git-radar](https://github.com/michaeldfallen/git-radar):

```sh
prompt_ssfprompt_vcs_status() { command git-radar --zsh }
```

Etc.
