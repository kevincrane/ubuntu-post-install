Ubuntu Post Install Scripts
===========================

A semi-automatic and interactive set of post-installation scripts for Ubuntu and its derivatives. You can use this project to install your favourite apps, set your preferred settings, and do minor housekeeping.

This project is free software; you can redistribute it and/or modify it under the terms of the [GNU General Public License](/LICENSE). If you have improvements, contributions to the [original](https://github.com/snwh/ubuntu-post-install) are much appreciated.

## Organization

This project is designed to be fairly modular (and not be one huge script) so you can easily delete or exclude bits/functions that you don't want to use.

 * [`data`](/data): files which are lists of packages<sup>&dagger;</sup> read by various functions.
 * [`functions`](/functions): the main functions of this scriptset. They should require little user-preference modification.
 * [`apps`](/functions/apps): functions for installing third-party applications. They are called in the [`install_thirdparty`](/functions/install_thirdparty) function.

*<sup>&dagger;</sup>These lists are preferential and you should to update them with packages you prefer*

## Adding Functions

Adding additional functions is as easy as editing one of the many already included functions and simply changing the variables. When you do add (or remove) functions be sure to update any main function (such as [`thirdparty`](/functions/thirdparty)) to reflect those changes.

## Usage

You use these scripts, you can just run the main script from the root of the source folder:

    ./ubuntu-post-install-script.sh

Alternatively, if you use `bash` and cloned this to your home folder, add the following to your `.bashrc` to run this script on-demand.

    export PATH=${PATH}:~/ubuntu-post-install/

## Where to make changes

* `data/config` - dotfiles; installed using `functions/setup_dotfiles`
* `functions/apps` - list of third-party apps and install steps; must also be added to list in `install_thirdparty`
* `functions/system_configure` - add one-off development configurations in function `dev_configure` (e.g. making python 3 the default)
* `data/*.list` - list of packages to be installed or removed in batches

For more detail, you can check in [`functions`](/functions/README.md) or the Organization section above.

## To-dos

* Add Sublime settings to `data/config/sublime_config.in`
* Add new development packages/libraries/programs
  * kubernetes, docker, etc
* Install Pycharm/IntelliJ via Snap
* Find more apps you need: https://snapcraft.io/store
* Create dotfiles from here: https://github.com/mathiasbynens/dotfiles
* Get `venva` command from work laptop, add to `data/config/bash_aliases.in`
* Fix PS1 in bashrc to be cleaner (just current directory) and git branch
* Add function for installing python packages (similar to `favs-dev`, but with `pip`)
* Install Flux
