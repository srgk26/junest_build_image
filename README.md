## Junest - https://github.com/fsquillace/junest

[Junest](https://github.com/fsquillace/junest) is a cool Arch Linux distro built by [Filippo Squillace](https://github.com/fsquillace/) that runs on any linux
 platform, wiht or without root privileges. This can be useful, for example when working on a remote server where you may need to install packages without goi
ng through your system administrator. Junest creates a fakeroot within your local user account, granting you full, unrestricted root privileges within your lo
cal user account (i.e. unrestricted privileges locally, not system-wide). It also means you can use your faourite Arch Linux distro within a Linux system runn
ing another distro.

This requires a junest system build image built from an existing Arch Linux system. The default junest image supplied by Filippo is outdated and building a ne
w junest system based on this image causes problems installing new software packages. The bets solution is to build your own system image, the instructions to
 which are also provided in his documentation.

This repo is simply me uploading my own latest junest build images that I will maintain and upload time-to-time. This is the build image I would use, and you 
are welcome to use this image too. The image build is merely system image, and does not contain any additional packages I have installed on my system.

## Junest installation instructions

This would be the instructions for you to install junest (which are also in Filippo's documentation) using my custom build junest build image:

```
## Downloading Junest
[guest@pc ~]$ git clone git://github.com/fsquillace/junest ~/.local/share/junest ## Downloads junest in your local system

## Add this line to ~/.bashrc
export PATH=~/.local/share/junest/bin:$PATH ## Adds junest to your PATH

## Downloading th latest junets system build image from this repo
[guest@pc ~]$ git clone https://github.com/srgk26/junest_build_image.git ## Clone this git repo
[guest@pc ~]$ cd junest_build_image/build_images ## Move into the directory containing junest build images

## Installing Junest
[guest@pc ~]$ junest -i junest-[date]-x86_64.tar.gz ## Replace date with the latest date available; This junest-[date]-x86_64.tar.gz is the custom junest system image from this repository.
```

## Custom build instructions

These are the junest image build instructions (which are also in Filippo's documentations):

This is in my system running Arch Linux:

```
## Downloading Junest
[user@pc ~]$ sudo pacman -Syu ## Perform system update first to build junest using the latest system image
[user@pc ~]$ sudo pacman -S arch-install-scripts
[user@pc ~]$ git clone git://github.com/fsquillace/junest ~/.local/share/junest

## Add this line to ~/.bashrc
export PATH=~/.local/share/junest/bin:$PATH

## Build system image
[user@pc ~]$ junest -b -n
```

This will give my own junest image with the same name, 'junest-x86_64.tar.gz'.

I will then export this image to my unprivileged Linux system, and execute these:

```
## Downloading Junest
[guest@pc ~]$ git clone git://github.com/fsquillace/junest ~/.local/share/junest

## Add this line to ~/.bashrc
export PATH=~/.local/share/junest/bin:$PATH

## Installing Junest
[guest@pc ~]$ junest -i junest-x86_64.tar.gz ## This junest-x86_64.tar.gz is the custom junest system image I built
```