# Linux-Documentation
Personal Linux hints and howtos

## Managing system disk space
Get 10 largest folders/files in path
```du -a /home/ziga | sort -n -r | head -n 10```
reference: https://www.cyberciti.biz/faq/linux-find-largest-file-in-directory-recursively-using-find-du/

## Terminal standard output to clipboard
First you have to install xclip <br/>
```sudo apt install xclip```

Then you can save any output to clipboard: <br/>
```cat ssh_key.pub | xclip -selection clipboard```


## Multi terminal windows in one window
-> TMUX (for customization (ctrl+a and mouse click) see tmux conf file in same repo)

For using tabs in tmux use (ctrl+a c) which opens a new tab. To swithc between them use (ctr+a <tab_index>)
To name each tab run inside tmux window session:
```tmux rename-window -t otherwindow newname```

For naming each window you can install xpanes
installation: https://github.com/greymd/tmux-xpanes/wiki/Installation

Common issue: all panes are synced by default
Solution: use default shortcut (ctrl + b) `:setw synchronize-panes off`

### For opening ssh connection and running htop on each ssh run:
```xpanes -e 'ssh -t dewe-db "htop"' 'ssh -t dewe-production "htop"' 'ssh -t dewe-antares "htop"'```

## (Un)Mounting file systems on system boot
etc/fstab
Example usage: Disable swp (swap)
https://www.redhat.com/sysadmin/etc-fstab

You can also disable swap for **current session** only by running: ```sudo swapoff -a```

## Enabling new aliases without closing terminal
When installing packages that are adding new aliases to our system, we usually want to use them in same terminal session.
This is possible with running command: ```source ~/.bashrc```
Although if you are using zsh or any other alternative to default bash terminal, make sure to source that config file instead.

## transfering files (directory) to remote server
Use command scp (secure copy).
```
sudo scp -r local_dir/ <USER>@<IP_ADDR>:<Destination_path>
```
Note: If you get permission denied, make sure that destination directory is owned by the same user you are transfering files with.
