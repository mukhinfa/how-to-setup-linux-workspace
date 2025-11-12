# Linux
## Tools
Самое базовое и нужное
```shell
sudo apt update && sudo apt upgrade -y && sudo apt autoremove

sudo apt install zsh curl wget tree bat zip unzip tar git gpg make build-essential gcc ripgrep eza -y

```
## zsh
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
    eza-zsh
    colorize
    command-not-found
    copyfile
    copypath
    dotenv
    golang
    gnu-utils
    iterm2
    man
    ssh
    sudo
)
```
add alias (optional)
```shell

alias ls='eza --tree --level=1 --icons=always --no-time --color=always --no-user --no-permissions'
```

Upd config
```shell
source ~/.zshrc
```
Set zsh as default
```shell
chsh -s /bin/zsh
```
## Nerd font for terminal & IDE
```shell
cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip JetBrainsMono.zip
fc-cache -fv
```
## Tools for dev

### VSCode
install deps
```shell
sudo apt install software-properties-common apt-transport-https wget -y
```
add Microsoft GPG key
```shell
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
```
add VSCode repo
```shell
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
```
install
```shell
sudo apt update
sudo apt install code
```

### Cursor
add GPG key
```shell
curl -fsSL https://packages.cursor.sh/linux/gpg.key | sudo gpg --dearmor -o /usr/share/keyrings/cursor-archive-keyring.gpg
```
add Cursor repo
```shell
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cursor-archive-keyring.gpg] https://packages.cursor.sh/linux/deb stable main" | sudo tee /etc/apt/sources.list.d/cursor.list
```
install
```shell
sudo apt update
sudo apt install cursor
```
### Postman
```shell
sudo snap install postman
```
### Docker
install deps
```shell
sudo apt install -y ca-certificates curl gnupg lsb-release
```
add Docker GPG key
```shell
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
add Docker repo
```shell
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
install
```shell
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
### Alacritty
install
```shell
sudo apt install -y alacritty
```
create dir
```shell
mkdir -p ~/.config/alacritty
```
clone
```shell
wget -O ~/.config/alacritty/alacritty.toml https://raw.githubusercontent.com/mukhinfa/how-to-setup-linux-workspace/master/configs/alacritty.toml
```


## Go
```shell
cd ~/Downloads
wget -O go_latest.tar.gz https://go.dev/dl/go1.25.4.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go_latest.tar.gz
rm go_latest.tar.gz

echo PATH=$PATH:/usr/local/go/bin >> ~/.zshrc

source ~/.zshrc

go version
```

## Git
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
