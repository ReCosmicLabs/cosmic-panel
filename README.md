# cosmic-panel (fork)

> **This is a fork of [pop-os/cosmic-panel](https://github.com/pop-os/cosmic-panel)**, the panel of the
> COSMIC desktop by [System76](https://system76.com). All credit for the panel itself goes to
> System76 and the upstream contributors. The license is unchanged: **GPL-3.0-only** (see `LICENSE.md`).

## Changes in this fork

Maintained by [eualexandrerrr](https://github.com/eualexandrerrr) for the
[dotfiles](https://github.com/eualexandrerrr/dotfiles) setup. Everything below is a modification of the
original work, as required by section 5 of the GPL.

- **`background_per_group`** (new key in `com.system76.CosmicPanel.Panel/v1`, default `false`). When set
  together with `expand_to_edges = true`, the panel draws no full-width background: each non-empty
  group (left, center, right) gets its own rounded pill, padded by `padding` and rounded by
  `border_radius`. Blur and the input region follow the pills too, so the rest of the layer is
  fully transparent and clicks between groups reach the desktop. Files touched: `cosmic-panel-config/src/panel_config.rs`,
  `cosmic-panel-config/src/container_config.rs`, `cosmic-panel-bin/src/space/{panel_space,layout,render}.rs`.
- **`exclusive_gap`** (new key, `u16` pixels, default `0`). Extra pixels added to the exclusive zone
  beyond the panel thickness, so maximized and tiled windows stop that far from the panel instead of
  touching it. Only used while `exclusive_zone` is on. File touched: `cosmic-panel-bin/src/space/panel_space.rs`.

Build: `cargo build --release -p cosmic-panel-bin`; the binary is `target/release/cosmic-panel`.
The dotfiles install it to `~/.local/bin`, ahead of the distro package.

---

Original README follows.

# Cosmic Panel (WIP)

### Building and Installing .deb

`dpkg-buildpackage -b -d`  
`cd ..`  
`sudo dpkg -i cosmic-panel_0.1.0_amd64.deb`  

### Configuring the panel / dock  
See the provided configs for the panel and dock in `data/default_schema`. 
The `com.system76.CosmicPanel` directory contains a key called entries, which is a list of profiles to be loaded. 
Each profile then has its own directory, for example, `com.system76.CosmicPanel.Panel`. 
You can make changes to the keys in this directory to alter the config. 
After making changes to copies of the provided config in data `data/`, you may install each to `$HOME/.config/cosmic/`
`find data/default_schema_copy -type f -exec install -Dm0644 {} {{$HOME/.config/cosmic}}/{} \;`

### Usage  
cosmic-panel

### Installing Plugins and Applets  
See the following for examples of applets and plugins which can be installed and used:  
https://github.com/pop-os/cosmic-applets  
 
