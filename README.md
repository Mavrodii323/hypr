# hypr

My [Hyprland](https://hypr.land/) configuration, written in the Lua config format
(`hyprland.lua`, Hyprland 0.57+). Single file, no external includes.

## Layout

| Section | What it does |
|---|---|
| `MONITORS` | `preferred` mode, scale `1.25` (1.5 on this HD 520 means rendering 2880×1620 and downsampling) |
| `MY PROGRAMS` | `foot`, `dolphin`, `hyprlauncher` |
| `AUTOSTART` | `qs -d -n` (Quickshell bar) |
| `LOOK AND FEEL` | dwindle layout, 1px gaps/borders, gradient active border, blur `size = 2`, shadow `range = 2` |
| `ANIMATIONS` | fast bezier curves; windows appear in 150 ms (`speed` is **deciseconds**) |
| `INPUT` | US layout, touchpad natural scroll, 3-finger gestures |
| `KEYBINDINGS` | see below |
| `WINDOWS AND WORKSPACES` | suppress-maximize, XWayland drag fix, `hyprland-run` popup rule |

## Keybinds

`SUPER` is the main modifier.

| Key | Action |
|---|---|
| `SUPER + Q` | terminal (foot) |
| `SUPER + C` | close window |
| `SUPER + M` | exit Hyprland (`hyprshutdown` if installed) |
| `SUPER + E` | file manager (dolphin) |
| `SUPER + R` | launcher (`hyprlauncher`, else `wofi`, else Quickshell bar) |
| `SUPER + A` | toggle Quickshell app launcher (`qs ipc call bar toggleLauncher`) |
| `SUPER + B` | Firefox |
| `SUPER + V` | toggle floating |
| `SUPER + P` | toggle pseudo-tile |
| `SUPER + SHIFT + P` | cycle power profile: performance → balanced → power-saver → auto |
| `SUPER + J` | toggle split (dwindle) |
| `SUPER + S` | toggle special workspace `magic` |
| `SUPER + SHIFT + S` | move window to `magic` |
| `SUPER + 1..0` | switch workspace |
| `SUPER + SHIFT + 1..0` | move window to workspace |
| `SUPER + arrows` | focus in direction |
| `SUPER + mouse down/up` | next/previous workspace |
| `SUPER + LMB/RMB drag` | move / resize window |
| `CTRL + SHIFT + S` | screenshot region (flameshot) |
| `XF86*` | volume, mute, mic mute, brightness, media keys |

## Notes

- Depends on: `foot`, `dolphin`, `quickshell` (`qs`), `flameshot`, `wpctl`
  (pipewire), `wofi`.
- Optional: `hyprlauncher` (preferred over `wofi`), `playerctl` (media keys
  fall back to raw MPRIS), `hyprshutdown`, `brightnessctl` (not needed —
  brightness uses logind).
- Local helpers in `~/.local/bin/`: `menu` (launcher fallback), `brightness`
  (logind backlight control, no root), `player` (media keys), `pp` (power
  profile).
- `SUPER + SHIFT + P` calls `~/.local/bin/pp cycle`; the automatic
  AC-aware profile is handled by the user unit `power-profile-auto.service`.
- Installed at `~/.config/hypr/hyprland.lua`.
- Reload after edits: `hyprctl reload`. Validate syntax first: `luac -p hyprland.lua`.
