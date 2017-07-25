# dotfiles

This is my system configuration for OS X consisting of config "dotfiles" and shell scripts.

## Usage

- Clone this repo to a directory in the $HOME folder;
- Run `cd dotfiles`
- Run `./dotfiles-setup.sh`.  This idempotent script will:
  - Initialize `/secrets` folder (repo).  This is a separate repo that contains secrets that will not be commited/push to the same remote as the main dotfiles repo. 
  - Create symlinks for all files and top level folders in $HOME/dotfiles.  For example, $HOME/.zshrc symlink will be created which will point to $HOME/dotfiles/.zshrc. 
  - Create additional symlinks for applications that do not store config in $HOME.  For example, a symlink will be created from /Library/Application Support/Code/User/settings.json to $HOME/.vscode.settings.json so that VS Code will use config residing in dotfiles, even though the original config location is outsite of $HOME.
  - Create symlinks for ssh key: `/.ssh/id_rsa > ${HOME}/secrets/id_rsa` and `/.ssh/id_rsa.pub > ${HOME}/secrets/id_rsa.pub` targeting key stored in $HOME/dotfiles/secrets.
  - Replace current user crontab with contents of `/.crontab`
- `dotfiles-link.sh` -  If there are files in $HOME that you would like to be moved to the dotfiles repo, you can run `dotfiles-link.sh` and pass in the name of the file that resides in $HOME.  This will move the file to `/home` and create a symlink to it. 

## Fresh OS X Setup

When setting up an OS X system initially, the following steps should be performed to get a base system setup.  **NOTE:** These steps should be performed before running `./setup.sh`
 
1. Install [Homebrew](http://brew.sh/) and then `brew install` the following packages:
   - git
   - lame
   - mysql
   - node
   - postgresql
   - gawk
   - vim
2. Install the shell helpers:
   - [RVM](https://rvm.io/rvm/install)
   - [NVM](https://github.com/creationix/nvm)
3. Install the following apps:
   - [Spectacle](https://www.spectacleapp.com/)
   - [Itsycal](https://www.mowglii.com/itsycal/)
   - [Status Clock](https://itunes.apple.com/us/app/status-clock/id552792489?mt=12)
   - [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12)
   - Xcode Command Line Tools - `xcode-select --install`
   - [iTerm2](https://www.iterm2.com/downloads.html)
   - [Zsh and Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH)
   - [Beyond Compare 4](http://www.scootersoftware.com/download.php) - Activation key in LastPass
   - [Navicat Essentials for PostgreSQL](https://www.navicat.com/download/navicat-essentials) - Activation key in LastPass
   - [Navicat Essentials for SQLite](https://www.navicat.com/download/navicat-essentials) - Activation key in LastPass
4. Configure:
   - [Honukai Theme for iTerm (forked)](https://github.com/bradyholt/honukai-iterm-zsh)
     - iTerm font [Meslo LG L DZ](http://github.com/andreberg/Meslo-Font/archive/master.zip)
   - Screenshots Folder
     - `mkdir ~/Screenshots`
     - `defaults write com.apple.screencapture location ~/Screenshots/`
     - `killall SystemUIServer`
   - [Use ⌥ ← and ⌥→ to jump forwards / backwards words in iTerm 2, on OS X](https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x)
