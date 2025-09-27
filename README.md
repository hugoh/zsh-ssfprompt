# zsh-ssfprompt: slim, simple, fast prompt for Zsh

This is prompt for zsh designed to be:
- Simple: only shows the information that matters
- Slim: fits on one line, with VCS information on the right and disappearing as needed
- Fast: expensive lookups are minimized and done asynchronously
- Simple implementation: heavily relies on existing libraries

It's likely going to evolve very little (if at all) functionality-wise.

[![asciicast](https://asciinema.org/a/286672.png)](https://asciinema.org/a/286672)

## Installation

The proper way to use it is to add the plugin to your `fpath` and then run:

```sh
autoload -U promptinit && promptinit
prompt ssfprompt
```

If you don't want to do it by hand, you can use a zsh plugin manager, such as [Zplugin](https://github.com/zdharma/zplugin):

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

### Left Prompt

Uses the `PROMPT` variable. You can define your own if desired.

### Right Prompt - Vi Mode Indicator + VCS Status Asynchronous Rendering

#### Vi Mode Indicator and Cursor

By default, ssfprompt displays a small Vi mode indicator on the right prompt ([N] when in normal mode) and switches the cursor shape (block in normal mode, vertical bar in insert mode).

You can disable both the indicator and the cursor shape changes via `zstyle`. Set this before loading the prompt:

```sh
zstyle ':prompt:ssfprompt' vi-mode off
```

#### VCS Status

Uses `prompt_ssfprompt_vcs_status` to display VCS status.

You can also override the Git status function to your liking by overriding `prompt_ssfprompt_vcs_status`.

##### Using Starship

To use [Starship](https://starship.rs/), configure the Git information to be in the right prompt and then:

```sh
prompt_ssfprompt_vcs_status() { command starship prompt --right }
```

With zsh-async installed, this will run Starship asynchronously to provide Git status – a workaround for [fetching Git status asynchronously with Starship](https://github.com/starship/starship/issues/301) –, assuming to have your right prompt configured as follows:

```toml
right_format = """
%F{yellow}\
$git_branch\
$git_commit\
$git_state\
%f\
%F{red}\
$git_status\
%f\
"""

[git_branch]
style = ''

[git_commit]
style = ''

[git_state]
style = ''

[git_status]
style = ''
```

##### Using gitHUD

To use [gitHUD](https://github.com/gbataille/gitHUD):

```sh
prompt_ssfprompt_vcs_status() { command githud zsh }
```

##### Using git-radar

To use [git-radar](https://github.com/michaeldfallen/git-radar):

```sh
prompt_ssfprompt_vcs_status() { command git-radar --zsh }
```
