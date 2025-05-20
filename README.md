# Papirus-Black

**A lean, blacked-out fork of the iconic [Papirus icon theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme).**

This repository builds on the original Papirus base and dark variants, removing all unused styles (Light, color folders, and redundant sizes) and surgically merging the required parts to create a lean, minimal, all-black version of Papirus-Dark. 

Result? 
- **350MB → 98MB** 
- Zero bloat, zero confusion. 
- Pure black folders across all desktop environments. 
- Full compatibility with both GTK and KDE.

---

## Why?

The original Papirus repo is brilliant but bloated. It carries legacy variants, hardcoded folder colors, and size duplicates. 

You get everything you need. Nothing you don’t.

---

## Installation

### Manual (All DEs)

Clone the repo and place it where your system can see icon themes:

```
git clone https://github.com/OrynVail/Papirus-Black.git
mkdir -p ~/.local/share/icons/
cp -r Papirus-Black ~/.local/share/icons/
gtk-update-icon-cache -f ~/.local/share/icons/Papirus-Black
```

Then activate it in your system’s appearance settings or run:

```
gsettings set org.gnome.desktop.interface icon-theme 'Papirus-Black'
```

### For NixOS Users

Add this to your home.nix:

```
customPapirusBlack = pkgs.stdenv.mkDerivation {
  pname = "papirus-dark-black";
  version = "1.0";
  src = ../../../themes/Papirus-Black;

  nativeBuildInputs = [ pkgs.gtk3 ];

  installPhase = ''
    mkdir -p $out/share/icons
    cp -r . $out/share/icons/Papirus-Black
    gtk-update-icon-cache -f $out/share/icons/Papirus-Black
  '';

  passthru.iconThemeName = "Papirus-Black";
};
```

Use iconTheme.name = "Papirus-Black"; wherever applicable.


### KDE Support

Plasma users should place it in:

```
~/.local/share/icons/
```

Apply it via System Settings → Appearance → Icons.

---

## Credit

 -  Original Icon Theme by the Papirus Development Team

 -  All original rights and trademarks belong to their respective owners.

 -  This repo repackages the GPLv3-licensed theme under open redistribution guidelines. No icons were harmed.
 
---

## License

Papirus icon theme is a free and open source project distributed under the terms of the GNU General Public License, version 3.
See the [`LICENSE`](LICENSE) file for details.

