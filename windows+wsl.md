# how-to-setup-windows

## Windows
```powershell
#Run in PowerShell as Administrator
#install choco
Set-ExecutionPolicy Bypass -Scope Process

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
#system
choco install vcredist140 vcredist2015 vcredist2010 vcredist2008 vcredist2017 vcredist2013 -y
#browser
choco install firefox googlechrome -y
#development
choco install git.install vscode cursoride docker-desktop dbeaver virtualbox postman -y

#other
choco install vlc audacity obs-studio.install sumatrapdf qbittorrent fsviewer zoom -y

wsl --install -d Ubuntu
wsl --set-default-version 2

Restart-Computer
```
## Linux
### Tools
```shell
sudo apt update && sudo apt upgrade -y && sudo apt autoremove

sudo apt install zsh curl wget tree bat zip unzip tar git gpg make build-essential gcc ripgrep -y

```
```shell
sudo mkdir -p /etc/apt/keyrings
wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
sudo apt update
sudo apt install -y eza
```

#### zsh
```shell
sudo apt install powerline fonts-powerline
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
nano ~/.zshrc
```
change theme
```shell
ZSH_THEME="agnoster"
```

Autosuggestions
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
nano ~/.zshrc
```
add plugin
```shell
plugins=(
    git
    z
    zsh-autosuggestions
    docker
    docker-compose
    history
    eza
    colorize
    command-not-found
    copyfile
    copypath
    dotenv
    golang
    gnu-utils
    man
    ssh
    sudo
)
```
add alias (optional)
```shell

alias ls='eza --tree --level=1 --icons=always --no-time --color=always --no-user --no-permissions'

alias ll='eza -la --icons --octal-permissions --group-directories-first'
alias l='eza -bGF --header --git --color=always --group-directories-first --icons'
alias llm='eza -lbGd --header --git --sort=modified --color=always --group-directories-first --icons' 
alias la='eza --long --all --group --group-directories-first'
alias lx='eza -lbhHigUmuSa@ --time-style=long-iso --git --color-scale --color=always --group-directories-first --icons'

alias lt='eza --tree --level=2 --color=always --group-directories-first --icons'
alias l.="eza -a | grep -E '^\.'"
```

Upd config
```shell
source ~/.zshrc
```
Set zsh as default
```shell
chsh -s /bin/zsh
```

### Go
```shell
cd ~/Downloads
wget -O go_latest.tar.gz https://go.dev/dl/go1.25.4.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go_latest.tar.gz
rm go_latest.tar.gz

echo PATH=$PATH:/usr/local/go/bin >> ~/.zshrc

source ~/.zshrc

go version
```

### Git
set global name & email
```shell
git config --global user.name "name"
git config --global user.email "your@email.com"
```
set VSCode as default git editor
```shell
git config --global core.editor "code --wait"
```
Color output configuration
```shell
git config --global color.ui auto
```
git push strategy
```shell
git config --global push.default simple
```

