# Configure crosh

1. Open crosh in a tab (ctrl-alt-t).
2. Open menu (upper right corner) -> more tools -> add to shelf
3. Right click on shelf icon, and select open as window.
4. Open developer tools (ctrl-shift-j), and paste the following:

```
// Reset all settings
term_.prefs_.resetAll()

// Set default terminal
term_.prefs_.set('environment', { TERM: "xterm-256color" })

// Disable bold 
term_.prefs_.set('enable-bold', true);
term_.prefs_.set('enable-bold-as-bright', false);

// Set cursor color
term_.prefs_.set('cursor-color', '#0f0');

// Use this for Solarized Dark 
term_.prefs_.set('background-color', "#002b36");
term_.prefs_.set('foreground-color', "#839496");

// Solarized Colors
term_.prefs_.set('color-palette-overrides', [
  '#073642', 
  '#dc322f', 
  '#859900', 
  '#b58900', 
  '#268bd2', 
  '#d33682', 
  '#2aa198', 
  '#eee8d5', 
  '#002b36', 
  '#cb4b16', 
  '#586e75', 
  '#657b83', 
  '#839496', 
  '#6c71c4', 
  '#93a1a1', 
  '#fdf6e3'
]);

// Font settings
term_.prefs_.set('font-family', '"Roboto Mono", monospace') 
term_.prefs_.set('font-size', 16)

// Disable scrollbar
term_.prefs_.set('scrollbar-visible', false);
```
