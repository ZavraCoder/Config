#Primero instalamos alacritty. Para ello instalamos las dependencias:
apt install cmake pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3
apt install fonts-font-awesome

#Clonamos el repositirio
https://github.com/alacritty/alacritty.git

#Instalamos rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

#Comprobamos que funciones bien
rustup override set stable
rustup update stable

#Ejecutamos el siguiente comando dentro del repositorio de alacritty
cargo build --release

#Ejecutamos el siguiente comando para comprobar que este bien:
infocmp alacritty

#En caso de error ejecutamos este:
sudo tic -xe alacritty,alacritty-direct extra/alacritty.info

#Configuramos los iconos:
sudo cp target/release/alacritty /usr/local/bin # or anywhere else in $PATH
sudo cp extra/logo/alacritty-term.svg /usr/share/pixmaps/Alacritty.svg
sudo desktop-file-install extra/linux/Alacritty.desktop
sudo update-desktop-database

#Instalamos los siguiente programas
bat(lo instalmos con apt) y lsd(lo instalmos con snap)

#Instalamos zsh
sudo apt install zsh
chsh -s $(which zsh)
--> Ahora cerramos sesion y volvemos a loggearnos para cargar bien zhs

#Instalamos oh-my zhs
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

#Tema zhs
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

#Pluggins:<br>
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions <br>
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting <br>

#Dentro de .zshrc Anyadimos los plugins
plugins=( [plugins...] zsh-syntax-highlighting, zsh-autosuggestions)

#Anyadimos los alias para bat y lsd dentro de .zhsrc
alias ls="lsd"
alias bat="/usr/bin/batcat"

#Cambiamos el tema en .zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"

#Anyadimos e instalamos neovim
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt update
sudo apt upgrade
sudo apt install neovim

#Instalamos vault
sudo apt install ansible -y
