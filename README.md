# dotfiles
My personal dotfiles following the [Atlassian bare repo tutorial](https://www.atlassian.com/git/tutorials/dotfiles)

# Setup 
1. Prevent weird recursion problems:
   ```zsh
   echo ".dotcfg" >> $HOME/.gitignore
   ```
2. Clone this dotfile repository into the `.dotcfg` folder of your `$HOME`:
   ```zsh
   git clone --bare git@github.com:snototter/dotfiles.git $HOME/.dotcfg
   ```
3. Define the following alias:
   ```zsh
   alias dotconfig='/usr/bin/git --git-dir=$HOME/.dotcfg/ --work-tree=$HOME'
   ```
4. TODO `dotconfig checkout` - might fail (need to automate user query + backup)
5. Set repository properties:
   ```zsh
   # Hide untracked files
   dotconfig config --local status.showUntrackedFiles no
   # User details
   dotconfig config --local user.name "snototter"
   dotconfig config --local user.email "snototter@users.noreply.github.com"
   ```
6. Done, now dotfile changes can be simply tracked:
   ```zsh
   dotconfig status
   dotconfig add .bashrc
   dotconfig commit -m "Add bashrc"
   dotconfig push
   ```
