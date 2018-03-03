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
- **Usuarios y groups > Arranque >** Spectacle, Flux

## Protege Safari
- Abre Safari 
- **Safari > Preferencias > General >** Deshabilita "Abrir archivos seguros al descargarlos"
- **Safari > Preferencias > Avanzado >** Habilita "Mostrar el menú Desarrollo en la barra de menús"

### Mostrar la carpeta Librería

```shell
chflags nohidden ~/Library
```

### Mostrar archivos ocultos

Tambien puedes hacerlo presionando la tecla `command` + `shift` + `.`.

```shell
defaults write com.apple.finder AppleShowAllFiles YES
```

### Mostrar la barra de path

```shell
defaults write com.apple.finder ShowPathbar -bool true
```

### Mostrar la barra de estado

```shell
defaults write com.apple.finder ShowStatusBar -bool true
```
