# Homenid

**Warning:** I'm a Nix/NixOS newbie. This is my playground for learning Nix.

A simple home manager for nix. Homenid doesn't use nix modules and is a single bash script.

Manages, files (dot files), fonts and systemd user services.

# Usage

Import Homenid into your user configuration (~/.config/nixpkgs/config.nix or an overlay), passing in the following parameters: `nixpkgs`, `files`, `services`, `fonts`.

`files` is a set, it's keys are the desired location in the home directory and it's value is an item (file or directory) located in the nix store.

```nix
files = {
    ".zshrc" = import ./zshrc.nix nixpkgs;
    ".zshenv" = ./zshenv;
  }
```

`services` is a set, it's keys are the names of the service and it's value is a service file located in the nix store.

```nix
files = {
    "mpd.service" = ./mpd.service
  };
```

**Warning:** Make sure that the service points to an actual `*.service` file.


`fonts` is a set, it's keys are the names of the font and it's value is a font directory located in the nix store.

```nix
fonts = {
    "MesloLGS" = ./mesloLGSNF;
    "siji" = "${nixpkgs.siji}/share/fonts/misc";
  };
```

Run Homenid

```sh
$ homenid
```
