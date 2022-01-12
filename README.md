# Linux-Documentation
Personal Linux hints and howtos

## Managing system disk space
Get 10 largest folders/files in path
```du -a /home/ziga | sort -n -r | head -n 10```
reference: https://www.cyberciti.biz/faq/linux-find-largest-file-in-directory-recursively-using-find-du/

## Multi terminal windows in one window
-> TMUX (for customization (ctrl+a and mouse click) see tmux conf file in same repo)
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
