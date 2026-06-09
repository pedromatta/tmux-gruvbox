<h1>Gruvbox theme for Tmux</h1>

This is a personal fork of [egel/tmux-gruvbox](https://github.com/egel/tmux-gruvbox) theme, customized to fit my personal preferences and terminal setup.

I've changed the default colors of the line sections and the display behaviour of the active window. I've also added a prefix highlight function, making the session section of the line change colors to show when the prefix is on.

## Installation

### Install via [TPM](github.com/tmux-plugins/tpm) (recommended)

Add plugin at the top list of TPM plugins list in `.tmux.conf` and select desired theme.

```bash
# ~/.tmux.conf

set -g @plugin 'tmux-plugins/tpm' # mandatory
set -g @plugin 'tmux-plugins/tmux-sensible' # optional recommended

set -g @plugin 'pedromatta/tmux-gruvbox'
set -g @tmux-gruvbox 'dark' # or 'light'

```

Hit `prefix + I` to fetch the plugin and source it. Your Tmux should be updated with the theme at this point.

### Install manually

1.  Clone the project to desired location

    ```bash
    cd ~/projects/
    git clone https://github.com/pedromatta/tmux-gruvbox.git
    ```

1.  Add theme at to top of your `~/.tmux.conf` config.

    ```bash
    # ~/.tmux.conf

    run ~/projects/tmux-gruvbox/tmux-gruvbox.tmux
    # set desired options...
    set -g @tmux-gruvbox 'dark' # or 'light'
    ```

## Configuration options


### Theme

- default value: `dark`

| Theme name | Color palette |
| :--------- | :------------ |
| `dark`     | 16-bit colors |
| `light`    | 16-bit colors |

```bash
set -g @tmux-gruvbox 'dark' # light
```

### Transparent status-bar

- default value: `'false'`
- tmux >= 3.2 (experimental)

```bash
set -g @tmux-gruvbox-statusbar-alpha 'true'
```

### Left Status (Section A)

- default value: `'#S'` (session name)

```bash
set -g @tmux-gruvbox-left-status-a '#S' # tmux's session name
```

### Prefix Highlight

When you press the tmux prefix key, the session block (Left Status A) and its divider dynamically change to a highlight color.

By default, this highlight uses the theme's blue color. You can customize the background and foreground colors for the prefix active state by setting:

```bash
# Set custom background color when prefix is active (e.g. orange)
set -g @tmux-gruvbox-prefix-bg '#fe8019'

# Set custom foreground color when prefix is active (e.g. dark grey)
set -g @tmux-gruvbox-prefix-fg '#282828'
```

### Right Status (Section X)

- default value: `'%Y-%m-%d'`

This section is customizable for user, and by default contains current date.

```bash
# set date in US notation
set -g @tmux-gruvbox-right-status-x '%m/%d/%Y' # e.g.: 01/31/2024
```

```bash
# or set date in EU notation
set -g @tmux-gruvbox-right-status-x '%d.%m.%Y' # e.g.: 30.01.2024
```

> [!TIP]
> Some user may have problem with displaying dates in desired format, if this
> case for you try using double percent `%%`

### Right Status (Section Y)

- default value: `'%H:%M'`

This section is customizable for user, and by default contains current time.

```bash
# set US time format
set -g @tmux-gruvbox-right-status-y '%I:%M %p' # 09:54 PM
```

### Right Status (Section Z)

- default value: `'#h'` (hostname)

This section is customizable for user, and by default contains hostname.

```bash
# display hostname and enhance section with other plugin
set -g @tmux-gruvbox-right-status-z '#h #{tmux_mode_indicator}'
```

> [!TIP]
> Make sure the themes' settings are defined before all other plugins,
> otherwise content from external plugins may not be displayed correctly by
> the theme.

## License

GPLv3 - Maciej Sypień
