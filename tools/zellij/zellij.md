# Basic Config

```
default_shell "zsh"
update_check_disable true
```

# Key Bindings

```
keybinds {
    // keybinds go here
}
```

# Basic (Normal Mode) Keybinds

```
normal {
    bind "Ctrl g" { SwitchToMode "locked"; }
    bind "Ctrl p" { SwitchToMode "pane"; }
    bind "Ctrl n" { NewPane; }
    bind "Ctrl h" { MoveFocus "Left"; }
    bind "Ctrl l" { MoveFocus "Right"; }
    bind "Ctrl j" { MoveFocus "Down"; }
    bind "Ctrl k" { MoveFocus "Up"; }
}
```

# Modes

```
Pane Mode: Ctrl + p
```

# Themes

```
themes {
    // themes go here
}

theme "theme-name"
```

## Default

```
theme
    default {
        fg "#d8dee9"
        bg "#2e3440"
        black "#3b4252"
        red "#bf616a"
        green "#a3be8c"
        yellow "#ebcb8b"
        blue "#81a1c1"
        magenta "#b48ead"
        cyan "#88c0d0"
        white "#e5e9f0"
        orange "#d08770"
    }
```

## Everforest

```
theme
    everforest {
        fg "#d3c6aa"
        bg "#2f383e"
        black "#4b565c"
        red "#e67e80"
        green "#a7c080"
        yellow "#dbbc7f"
        blue "#7fbbb3"
        magenta "#7a8478"
        cyan "#83c092"
        white "#d3c6aa"
        orange "#e69875"
    }
```
 
## Tokyo Night

```
theme
    tokyonight {
        fg "#c0caf5"
        bg "#1a1b26"
        black "#15161e"
        red "#f7768e"
        green "#9ece6a"
        yellow "#e0af68"
        blue "#7aa2f7"
        magenta "#bb9af7"
        cyan "#7dcfff"
        white "#a9b1d6"
        orange "#ff9e64"
    }
```
