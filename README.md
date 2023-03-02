# qemu-android-cm-x86

Pacote AUR [qemu-android-cm-x86](https://aur.archlinux.org/packages/qemu-android-cm-x86)  
Pacote AUR original: [qemu-android-x86](https://aur.archlinux.org/packages/qemu-android-x86)  
github original: [qemu-android-x86, autor: refutationalist](https://github.com/refutationalist/saur/tree/master/qemu-android-x86)  

## Instalação, usando makepkg:  

```
git clone https://aur.archlinux.org/qemu-android-cm-x86.git
cd qemu-android-cm-x86
sudo pacman -S inkscape
makepkg -si --needed --noconfirm 
mkdir -p ~/.config/android-x86
cp -av /usr/share/android-x86/config ~/.config/android-x86
```

## Instalação, usando yay (mais fácil):  

```
yay -S qemu-android-cm-x86
mkdir -p ~/.config/android-x86
cp -av /usr/share/android-x86/config ~/.config/android-x86
```

## Usando outros Android OS a partir do [qemu-android-cm-x86](https://aur.archlinux.org/packages/qemu-android-cm-x86)  

Foi testado 2 melhores versões de sistemas Android 11 usando este pacote como base.  
Se quiser testar ou usar também, siga as instruções das mesmas:  

1) [qemu-android-primeos-x86](https://github.com/elppans/qemu-android-primeos-x86/blob/main/README.md)  
2) [qemu-android-blissos-x86](https://github.com/elppans/qemu-android-blissos-x86/edit/main/README.md)  
