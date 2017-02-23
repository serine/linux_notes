# ssh 

- `ssh-add -l` -  to list all available agents (keys)

- `ssh-agent tmux` - to start BASH process that will keep you ssh keys around so that you wouldn't have to enter you passpharse all the time
- `ssh-add .ssh/bypass` - to add a key 

now you can simply open new tmux window and you'll be able to ssh without needing to enter your passphrase

- `ssh-copy-id -i your.pub kirill@blah.com` to copy ssh public key across

- tuneling `ssh -L 8787 localhost:8787 pavel@bioinformatics.erc.monash.edu`

