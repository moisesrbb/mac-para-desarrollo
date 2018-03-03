# Configurar una Mac para desarrollo web
Desde hace ya un tiempo que tengo una Mac mini y una Macbook Air y ha sido todo un reto encontrar la configuración adecuada para usar mi Mac para programar y crei que seria buena idea tomar algunas notas y compartirlas, pero sobre todo para que no se me olvido a mi :D

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
