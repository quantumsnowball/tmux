# Tmux Config Ready to Clone and Deploy

Tmux is very essential to my terminal workflow. So I want to make setting up tmux configs as simple as just one single git clone command!

# Installation

Tmux accept a config files located at `~/.config/tmux/tmux.conf`. Just clone this repo into `~/.config` and the tmux can find it.

```
cd ~/.config
git clone https://github.com/quantumsnowball/tmux
```

Restart tmux and the new configs should be sourced automatically.

# Startup

You can create a new or join an existing tmux session upon launch a terminal. Put the following command as terminal launch option:

```
bash -c "tmux attach -t 0 || tmux new -s 0"
```
Or like this if you use WSL2:

```
C:\Windows\system32\wsl.exe -d Arch --exec bash -c "tmux attach -t 0 || tmux new -s 0"
```

