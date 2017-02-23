My Dell Log
----------------------------------------------------------------------------------------------------

  This is log of all the tweaks I have done to my Dell - Ubuntu machine a.k.a biostation
  Two main reasons for this:

  1. Easy to reproduce the same OS
  2. Easy to troubleshoot if and when probblems might arise

Installed Ubuntu 14.04 from usb drive
----------------------------------------------------------------------------------------------------

I have re-installed `ubuntu-14.04.2-desktop-amd64.iso` to MyDell `LATITUDE E7440` in UEFI mode now.
This is [askubuntu thread](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/) that
described step by step approach how to make EFI only bootable usb. Basically is comes down to this one line
of code `$ 7z x ubuntu-12.04-desktop-amd64.iso -o/media/$USER/604A-00EA/`

I then wrote bash script that basically installed all the essentials for me in one hit.

``` BASH
ESSENTIALS=(ubuntu-restricted-extras \
	    vlc \
	    clementine \
	    python \
	    python-pip \
	    ipython \
	    python-biopython \
	    python-matplotlib \
	    curl \
	    vim \
	    r-base 
	    git \
	    tmux \
	    sl \
	    mosh \
	    htop \
	    dconf-editor \
	    libgnome2-bin \
	   )

GETRIDOFF=(rhythmbox \
	   unity-webapps-common \
	  )

echo sudo apt-get remove --purge ${GETRIDOFF[*]} && \
echo sudo apt-get autoremove && \
echo sudo apt-get autoclean && \
echo sudo apt-get update && \
echo sudo apt-get upgrade && \
echo sudo apt-get autoremove && \
echo sudo apt-get autoclean && \
echo sudo apt-get install ${ESSENTIALS[*]}  && \
echo sudo apt-get update && \
echo sudo apt-get upgrade && \
echo sudo apt-get -f install && \
echo sudo apt-get autoremove && \
echo sudo apt-get autoclean && \
echo sudo reboot 
```
----------------------------------------------------------------------------------------------------

- to check 3D use the following `/usr/lib/nux/unity_support_test -p`

Download lates .deb packages for:

 1. google-chrome
 2. RStudio

`dpkg -i whatever.deb`
`sudo apt-get install -f`

----------------------------------------------------------------------------------------------------

The automount-open feature had been disabled. Here are the steps:

 - use `dconf-editor` to turn that feature off. If `dconf-editor` not installed, then `sudo apt-get install` it
 - find `org.gnome.desktop.media-handling` and untick relevant box

- To change a font settings system wide use command below. Default font size is 11, I believe
`sudo gsettings set org.gnome.desktop.interface font-name 'Sans 11'`

----------------------------------------------------------------------------------------------------

`pandas` was intalled using `sudo pip install pandas` 
it required the following dependencies `sudo apt-get install python-dev libxml2-dev libxslt-dev`

----------------------------------------------------------------------------------------------------

set your history per directory
watch for this new file appearing in every directory now `.dir_bash_history`
follow this link to get it workign https://gist.github.com/leipzig/1651133

----------------------------------------------------------------------------------------------------

## Setting up virtual box

- `sudo apt-get install virtualbox`
- `sudo usermod -aG vboxusers <username>` to enablel USB support in virtualbox

----------------------------------------------------------------------------------------------------

# Old specs

installed bcbio-nextgen by `pip install bcbio-nextgen`
I need it to convert bam to wiggle file.
I also had to install separate binary wigToBigWig into /opt/ diractory and added to the PATH
In order to add to the PATH
I appended `export PATH="/opt/:$PATH"` to ~/.bashrc file and run `source ./bashrc` to restart it

this are dependencies for bcbio-nextgen `sudo apt-get install libxml2-dev libxslt1-dev python-dev`


I have been give account on bioinformatics platform server, but at this stage it dosen't have a
a domain name, just the IP. David showed me how to make a shortcut. I went into .ssh file and
pasted this into it

 Host bioinformatics-platform
 Hostname 118.138.240.158
 User kirill

now when I  need to log onto the machine I can just type bio and tab expand into bioinformatics-
platform

*Installing R-studio from source*


*New NeCTAR instance*

1. Import public ssh key onto NeCTAR, under `Access & Security` under `Key Pairs` tab.
2. Then launch a new instance
3. Enable `Security Groups` under `Instances` -> `more` -> `Edit Security Groups`
4. ssh ubuntu@`ip address` provided you have launched ubuntu instances.

## Ubuntu 16.04 LTS (Xenial Xerus)

I did fresh install

```BASH
sudo apt-get install vim \
                     vim-gnome \
                     tmux \
                     git \
                     zsh \
                     htop
```

ran `sudo chsh` to `/bin/zsh`

```BASH
sudo apt-get remove --purge rhythmbox
sudo apt-get install clementine \
                     vlc \
                     ubuntu-restricted-extras
```

```BASH
# to remove amazon unity lens
sudo apt-get remove unity-webapps-common
sudo apt-get autoremove
```

```BASH
# setting workstations layout
sudo gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hsize 4
sudo gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ vsize 1
```

- added unimelb R mirror and installed latest R
- installed `google-chrome`
- installed `RStudio`
- installed `slack`

#### Inside `/opt` directory

- node.js
- IGV
- mongoDB

all symlink to `/usr/local/bin`

#### 

- installed [copyQ](https://github.com/hluk/CopyQ/releases) by downloading `*.deb` package and `dpkg -i` cmd

####

- use `rm -r /var/lib/apt/lists/*` to remove all of the fetched URLs and packages and then re-run `apt-get update` to get new ones
- `sudo apt-get remove update-notifier update-notifier-common` this stops random pop ups for the update

#### Bugs

- `appstreamcli refresh` [here is the fix](http://askubuntu.com/questions/774986/appstreamcli-is-overheating-my-laptop-what-is-it)
