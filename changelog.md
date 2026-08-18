# 0.0.10 — "meast"

Released: 2026-08-18

- Improved the visual consistency of the interface: the main window frame and the containers behind interactive controls now use a rounded-square corner radius of 12.
- Refined buttons and sliders with subtle rounded-square corners to match the updated design language.
- Retained the classic circular knob design for toggles with no visual regression.
- Removed the GitHub icon and version title from the Window:Tag definitions in main.client.lua and main2.client.lua.
- Removed the hard-coded version badge from the client examples.
- Removed the redundant backup file src/themes/Init.lua.bak from version control.
- Expanded the README into a comprehensive reference covering installation, window configuration, window methods, every element, theming, the configuration/Flag system, and building from source.
- Corrected several documented configuration keys to match the public API (Toggle.Value, Dropdown.Value, Input.InputIcon).
- Updated build.sh to automatically download the darklua binary when it is not installed, so npm run build works without manual setup.
- Extended .gitignore to exclude backup files and build-cache artifacts.
- Bumped the version to 0.0.10 across package.json, build/package.lua, and src/Init.lua, and rebuilt dist/main.lua.

---

# 1.6.66
# 1.6.66

## Changelog

- added `CodeSize: number`, `CodeTheme: table`, `CanCopied: boolean` and `Height: UDim` to [Code](https://footagesus.github.io/treehub-web/docs/nexoui/code) element (#91)
- changed PandaDev API url in [Key System](https://footagesus.github.io/treehub-web/docs/nexoui/keysystem) (#92)
- fixed [Section](https://footagesus.github.io/treehub-web/docs/nexoui/sections) bg (in custom themes)
- fixed [Colorpicker](https://footagesus.github.io/treehub-web/docs/nexoui/colorpicker) issue
- fixed `Viewport` bug when u can pinch it outside
- fixed [Window](https://footagesus.github.io/treehub-web/docs/nexoui/window) Drag with multiple fingers (#79)
- added `ProgressBar` element (#95 by [BitRevenant](https://github.com/BitRevenant)) [Github PR](https://github.com/SirAsta/NexoUI/pull/95)
- fixed `Dropdown.Locked` (#94 by [BitRevenant](https://github.com/BitRevenant)) [Github PR](https://github.com/SirAsta/NexoUI/pull/94)
