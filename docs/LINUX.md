# Linux Installation Instructions

## AppImage

Download the AppImage and type the following:

1. `chmod +x marktext-%version%-x86_64.AppImage`
2. `./marktext-%version%-x86_64.AppImage`
3. Now you can execute Mark Text.

### Installation

You cannot really install an AppImage. It's a file which can run directly after getting executable permission. To integrate it into desktop environment, you can either create desktop entry manually **or** use [AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher).

#### Desktop file creation

See [example desktop file](https://github.com/marktext/marktext/blob/develop/resources/linux/marktext.desktop).

```bash
$ curl -L https://github.com/marktext/marktext/blob/develop/resources/linux/marktext.desktop -o $HOME/.local/share/applications/marktext.desktop

# Update the Exec in desktop file to your real marktext command. Specify Path if necessary.
$ vim $HOME/.local/share/applications/marktext.desktop

$ update-desktop-database $HOME/.local/share/applications/
```

#### AppImageLauncher integration

You can integrate the AppImage into the system via [AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher). It will handle the desktop entry automatically.

### Uninstallation

1. Delete AppImage file.
2. Delete your desktop file if exists.
3. Delete your user settings: `~/.config/marktext`

### Custom launch script

1. Save AppImage somewhere. Let's say `~/bin/marktext.AppImage`
2. `chmod +x ~/bin/marktext.AppImage`
3. Create a launch script:
   
   ```sh
   #!/bin/bash
   DESKTOPINTEGRATION=0 ~/bin/marktext.AppImage
   ```

### Known issues

- Mark Text is always integrated into desktop environment after updating

## Binary

You can download the latest `marktext-%version%.tar.gz` package from the [release page](https://github.com/marktext/marktext/releases/latest). You may need to install electron dependencies.

## Flatpak

### Installation

**Prerequisites:**

You need to install the `flatpak` package for your distribution. Please see the [official flatpak tutorial](https://flatpak.org/setup/) for more information and note that you have to add the flathub repository (`flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`) as described in the Quick Setup.

**Install from Flathub:**

After you install flatpak and flathub repository, you can install [Mark Text](https://flathub.org/apps/details/com.github.marktext.marktext) with just one command (note that you may be asked to enter your password):

```
flatpak install flathub com.github.marktext.marktext
```

or `flatpak install --user flathub com.github.marktext.marktext` to install for the current user only.

To run Mark Text just execute `flatpak run com.github.marktext.marktext` or click on the Mark Text icon in your application launcher.

### Update

To update Mark Text run the following command:

```
flatpak update com.github.marktext.marktext
```

or `flatpak update` to update all installed flatpaks.
