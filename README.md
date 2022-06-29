# Tmux Config Ready to Clone and Deploy

Tmux is very essential to my terminal workflow. So I want to make setting up tmux configs as simple as just one single git clone command!

# Installation

Tmux accept a config files located at `~/.config/tmux/tmux.conf`. Just clone this repo into `~/.config` and the tmux can find it.

```
cd ~/.config
git clone https://github.com/quantumsnowball/tmux
```

Restart tmux and the new configs should be sourced automatically.

# Initial Setup from Scratch

Currently my config is based on Oh-my-tmux config. I have done the following modifications to make Oh-my-tmux follow XDG_CONFIG_HOME standards.

1. Clone this repo into you config home (i.e. ~/.config).

```
cd ~/.config
git clone https://github.com/quantumsnowball/tmux
```

2. Clone Oh-my-tmux inside this repo for reference and future updates.

```
cd ~/.config/tmux
git clone https://github.com/gpakosz/.tmux.git
```

3. Copy the useful files to tmux default location.

```
# defaults
cp .tmux/.tmux.conf tmux.conf

# user configs, use the template or provide your own existing tmux.conf.local
cp .tmux/.tmux.conf.local tmux.conf.local
```

4. Edit `tmux.conf` to source `~/.config/tmux/tmux.conf.local` instead of the default.

```
# Look for the following lines in tmux.conf

# change 
bind r source-file ~/.tmux.conf \; display '~/.tmux.conf sourced'
# to
bind r source-file ~/.config/tmux/tmux.conf \; display '~/.config/tmux/tmux.conf sourced'

# change 
source -q ~/.tmux.conf.local
# to
source -q ~/.config/tmux/tmux.conf.local

# change 
bind e new-window -n "~/.tmux.conf.local" "EDITOR=\${EDITOR//mvim/vim} && EDITOR=\${EDITOR//gvim/vim} && \${EDITOR:-vim} ~/.tmux.conf.local && tmux source ~/.tmux.conf && tmux display \"~/.tmux.conf sourced\""
# to
bind e new-window -n "~/.config/tmux/tmux.conf.local" "EDITOR=\${EDITOR//mvim/vim} && EDITOR=\${EDITOR//gvim/vim} && \${EDITOR:-vim} ~/.config/tmux/tmux.conf.local && tmux source ~/.config/tmux/tmux.conf && tmux display \"~/.config/tmux/tmux.conf sourced\""
```

# About

The purpose of this modifications is to pack all tmux configs into one single public repository, such that when you need to quickly setup up a new machine, your can clone this repo to the config and apply all the awesome settings right away. Currently I use Oh-my-tmux, so I make this little hack to make it lives under its own directory, but in the future this may change.
