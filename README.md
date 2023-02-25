# qemu-android-cm-x86

Pacote AUR [qemu-android-cm-x86](https://aur.archlinux.org/packages/qemu-android-cm-x86)  
Pacote AUR original: [qemu-android-x86](https://aur.archlinux.org/packages/qemu-android-x86)  
github original: [qemu-android-x86, autor: refutationalist](https://github.com/refutationalist/saur/tree/master/qemu-android-x86)  

Instalação:  

Usando makepkg:  

```
git clone https://aur.archlinux.org/qemu-android-cm-x86.git
cd qemu-android-cm-x86
sudo pacman -S inkscape
makepkg -si --needed --noconfirm 
mkdir -p ~/.config/android-x86
cp -av /usr/share/android-x86/config ~/.config/android-x86
```

Usando yay (mais fácil):  

```
yay -S qemu-android-cm-x86
mkdir -p ~/.config/android-x86
cp -av /usr/share/android-x86/config ~/.config/android-x86
```

# Configurando [BlissOS](https://blissos.org/) com qemu-android-cm-x86:

Esta configuração depende do pacote [qemu-android-cm-x86](https://aur.archlinux.org/packages/qemu-android-cm-x86)  
Após a instalação do pacote, faça o prossedimento a seguir, para usar o BlissOS no [QEMU](https://www.qemu.org/):  
Nesta configuração, será usado a versão 14.10, mas pode fazer o mesmo procedimento para a versão 15.

```
cd ~/Downloads
wget -c https://sourceforge.net/projects/blissos-dev/files/Beta/Bliss-v14.10-x86_64-OFFICIAL-foss-20230201.iso
mkdir -p blissos ~/.config/android-x86/blissos
sudo mount -o loop Bliss-v14.10-x86_64-OFFICIAL-foss-20230201.iso blissos/
cp -av blissos/initrd.img blissos/kernel blissos/system.sfs ~/.config/android-x86/blissos
cp -av /usr/share/android-x86/config ~/.config/android-x86/blissos
cp -av /usr/bin/qemu-android ~/.config/android-x86/blissos/qemu-android-blissos
sed -i 's/android-x86\//android-x86\/blissos\//' ~/.config/android-x86/blissos/qemu-android-blissos
sed -i '/DATASIZE/s/#//' ~/.config/android-x86/blissos/config
sed -i "/DATASIZE/s/2048/$(expr 1024 \* 60)/" ~/.config/android-x86/blissos/config
echo -e '
# Custom for r/w system images:
SYSTEMIMG="$HOME/.config/android-x86/blissos/system.sfs"
INITRD="$HOME/.config/android-x86/blissos/initrd.img"
RAMDISK="$HOME/.config/android-x86/blissos/ramdisk.img"
KERNEL="$HOME/.config/android-x86/blissos/kernel"
' | tee -a ~/.config/android-x86/blissos/config
truncate -s 2048K ~/.config/android-x86/blissos/ramdisk.img
sudo umount blissos
```

* A 2ª linha do comando `sed`  do parâmetro `DATASIZE` é para adicionar o cálculo para 60 GB de criação do arquivo **`data.img`**
Troque 60 para o tamanho que quiser, ao fazer o comando.  

### Testando o comando para o BlissOS

```
~/.config/android-x86/blissos/qemu-android-blissos gui
```

### Customizando arquivo .desktop

```
sudo ln -sf ~/.config/android-x86/blissos/qemu-android-blissos /usr/bin/qemu-android-blissos
cp -av /usr/share/applications/qemu-android.desktop ~/.local/share/applications/qemu-android-blissos.desktop
sed -i 's/qemu-android/qemu-android-blissos/' ~/.local/share/applications/qemu-android-blissos.desktop
sed -i 's/-blissos.png/.png/' ~/.local/share/applications/qemu-android-blissos.desktop
```

Após a configuração, basta clicar no ícone que aparecerá em seu menú.

