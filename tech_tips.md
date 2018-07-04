Set locale in ubuntu machine

```
export LC_ALL="en_US.UTF-8"
```

How to fix - zsh: corrupt history file /home/myusername/.zsh_history

```
mv .zsh_history .zsh_history_bad
strings .zsh_history_bad > .zsh_history
fc -R .zsh_history
```
