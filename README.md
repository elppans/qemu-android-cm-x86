# qemu-android-cm-x86

Pacote AUR [qemu-android-cm-x86](https://aur.archlinux.org/packages/qemu-android-cm-x86)  
Pacote AUR original: [qemu-android-x86](https://aur.archlinux.org/packages/qemu-android-x86)  
github original: [qemu-android-x86, autor: refutationalist](https://github.com/refutationalist/saur/tree/master/qemu-android-x86)  

Instalação:  

Usando makepkg:  

```
git clone https://aur.archlinux.org/qemu-android-cm-x86.git
cd qemu-android-cm-x86
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
