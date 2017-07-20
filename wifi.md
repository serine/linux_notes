
## Reloading wifi kernel module 

```BASH
sudo lshw -C network 2>&1 | grep wireless | grep driver
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```
