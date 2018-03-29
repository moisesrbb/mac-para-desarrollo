# Configurar una Mac para desarrollo web
Desde hace ya un tiempo que tengo una Mac mini y una Macbook Air y ha sido todo un reto encontrar la configuración adecuada para usar mi Mac para programar y crei que seria buena idea tomar algunas notas y compartirlas, pero sobre todo escribo esto para que no se me olvide :D

## Contenido

- [Preferencias del sistema](#preferencias-del-sistema)
- [Protege Safari](#protege-safari)
- [Xcode Command Line Tools](#xcode-command-line-tools)
- [Homebrew](#homebrew)
  - [Mac App Store command line interface](#mac-app-store-command-line-interface)
- [Apache](#apache)
- [PHP](#php)
- [MariaDB](#mariadb)

## Preferencias del sistema
- **Trackpad >** Habilitar "Presionar para hacer clic"
- **Accesibilidad > Mouse y trackpad > Opciones del trackpad >** Habilitar "Activar arrastre (arrastrar con 3 dedos)"
- **Teclado > Texto >** Deshabilitar "Corregir ortografía automáticamente".
- **Teclado > Repetición de tecla >** Rápida (todo hasta la derecha)
- **Teclado > Espera hasta la repetición >** Corta (todo hasta la derecha)
- **Seguridad y privacidad > Firewall >** Activar firewall
- **Seguridad y privacidad > General >** Seleccionar "App Store y desarrolladores indentificados"
- **Compartir > Compartir archivos** Deshabilitar
- **Usuarios y groupos > Arranque >** Spectacle, Flux

### Mostrar la carpeta Librería

```shell
chflags nohidden ~/Library
```

### Mostrar archivos ocultos

```shell
defaults write com.apple.finder AppleShowAllFiles YES
# ó presionando la tecla `command` + `shift` + `.`
```

### Mostrar la barra de path

```shell
defaults write com.apple.finder ShowPathbar -bool true
```

### Mostrar la barra de estado

```shell
defaults write com.apple.finder ShowStatusBar -bool true
```

### Mostrar las extensiones de los archivos

```shell
defaults write -g AppleShowAllExtensions -bool true
```

### Mostrar el path en la barra de titulo

```shell
defaults write com.apple.finder _FXShowPosixPathInTitle -bool true
```

### Mantenlos limpios

```shell
# Evita la creación de archivos duplicados y .DS_Store en volumenes de red
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true

# Evita la creación de archivos duplicados y .DS_Store en dispositivos USB
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true
```

### Capturas de pantalla

```shell
# Guardar capturas en un directorio predetreminado, en mi caso "screenshots"
mkdir ~/screenshots
defaults write com.apple.screencapture location ~/Desktop/screenshots/ && \
killall SystemUIServer

# Establecer un formato: png, jpg, jpeg, gif, pdf o tiff
defaults write com.apple.screencapture type -string "png"

# Deshabilita sombras en las capturas
defaults write com.apple.screencapture disable-shadow -bool true && \
killall SystemUIServer
```

## Protege Safari
- Abre Safari 
- **Safari > Preferencias > General >** Deshabilita "Abrir archivos seguros al descargarlos"
- **Safari > Preferencias > Avanzado >** Habilita "Mostrar el menú Desarrollo en la barra de menús"

## Xcode Command Line Tools
Si aún no lo tienes, busca e instala desde la **Mac Apps Store** la versión mas reciente de **Xcode**. Necesitaras abrirlo al menos una vez para aceptar los terminos y condiciones antes de poder ejecutar los siguientes comandos. Abre una terminal y ejecuta:

```shell
xcode-select --install
```

## Homebrew
Homebrew es un manejador de paquetes que nos ayudara a instalar algunas de las herramientas mas poderosas o necesarias que necesitaras usar desde la línea de comando. **Cask** es una extensión de Homebrew que nos permitira instalar aplicaciones de escritorio.

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Lo siguiente es indicarle al sistema que use las versiones de las aplicaciones instaladas por Homebrew, para esto necesitamos agregar la siguiente línea en el PATH de tu _.bash_profile_

```shell
export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"

# ó ejecuta lo siguiente si aún no has creado tu archivo _.bash_profile_
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
```

Antes de comenzar a usar Homebrew para instalar aplicaciones, agreguemos este alias a nuestro _.bash_profile_ que nos ayudara a darle el mantenimiento a nuestro Homebrew, sus formulas y las aplicaciones que hemos instalado

```shell
echo "alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'" >> ~/.bash_profile

# ahora cargamos los cambios con
source ~/.bash_profile
```

Ahora instalamos **cask** que como ya comente, nos servira para instalar aplicaciones de escritorio.

```shell
brew tap caskroom/cask
```

Y ahora actualizamos todas las formulas y aplicaciones de nuestro Homebrew, para poder comenzar a utilizarlo, no es necesario pero siempre me gusta tener las versiones más nuevas.
```shell
brewup
```

Hay dos formas de instalar aplicaciones usando **Brew**, el siguiente comando instala **Google Chrome**:

```shell
brew cask install google-chrome
```

La segunda es creando un archivo y poniendo en el, la lista de aplicaciones que queremos instalar

```shell
touch ~/Brewfile
```

Esta es la lista de aplicaciones que contiene mi archivo

```shell
cask 'firefox'
cask 'dropbox'
cask 'gimp'
cask 'vlc'
cask 'vagrant'
cask 'vagrant-manager'
cask 'virtualbox'
cask 'font-source-code-pro'
cask 'transmit'
cask 'visual-studio-code'
brew 'bash-completion'
brew 'tree'
cask 'flux'
cask 'dash'
cask 'kindle'
cask 'steam'
```

Ahora ejecutamos el siguiente comando y esperamos mientras **Brew** instala todo por nosotros.

```shell
brew bundle install
```

### Mac App Store command line interface
Instalemos nuestra primera aplicación con Hombrew, Mac App Store command line interface es una aplicación que nos ayudara a re-instalar las aplicaciones de la Mac App Store que hallamos comprado anteriormente, desde línea de comando.

```shell
brew install mas
```

Para poder comenzar a usar **mas-cli** necesitamos primero _iniciar sesión_, usando el siguiente comando:

```shell
mas signin correo_con_que_registraste_tu_apple_id@email.com
```

Una vez que hallas iniciado sesión, ya podemos re-instalar nuestras aplicaciones con **mas-cli**

```shell
#instalar Pages
mas install 409201541

#instalar Numbers
mas install 409203825

#instalar Keynote
mas install 409183694
```

Para más información de como usar **mas-cli** visita su [página oficial](https://github.com/mas-cli/mas).

## Apache

## PHP

## MariaDB
