<div align="center">

# Ouu shi

A modern, open-source **Roblox UI Library** built for script hubs inspired by [WindUI](https://github.com/Footagesus/WindUI).

**v0.0.7** · **MIT License** · [GitHub](https://github.com/SirAsta/NexoUI)
the readme is basically ai slop tbf im not writing one

</div>

---

> [!NOTE]
> **NexoUI is inspired by [WindUI](https://github.com/Footagesus/WindUI).**

> [!WARNING]
> **NexoUI is currently in Beta.**
> This project is still under active development. Bugs, issues, and unstable features may occur. We're constantly working on improvements, so please be patient and report any problems you encounter.

---

## 📖 Table of Contents

- [Features](#-features)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Window Configuration](#-window-configuration)
- [Theming](#-theming)
- [Elements](#-elements)
- [Configuration System (Flags)](#-configuration-system-flags)
- [Building from Source](#-building-from-source)
- [Project Structure](#-project-structure)
- [Credits](#-credits)

---

## ✨ Features

- 🪟 **Fully featured window** with tabs, sections, groups, a title bar, topbar buttons, search, and a draggable / resizable layout.
- 🎨 **Beautiful, modern design** with rounded-square (small UI corners) buttons, sliders, and element cards.
- 🔘 **Many built-in elements**: Button, Toggle, Checkbox, Slider, ProgressBar, Keybind, Input, Dropdown, Colorpicker, Code, Divider, Space, Image, Section, Group, HStack, VStack, Viewport and more.
- 🎭 **Theming + localization** — built-in themes (e.g. `"Dark"`, `"Mellowsi"`) and language switching out of the box.
- 🎮 **Acrylic blur** and gradient support.
- 📁 **Config system** with `Flag`-based saving / loading of element states.
- 🔔 **Notifications & Popups**.
- 🖱️ **Open button**, toggle key binding, lock/unlock elements, hover highlights.

---

## 📦 Installation

### Option 1 — Loadstring (recommended for executors)

```luau
loadstring(game:HttpGet('https://raw.githubusercontent.com/SirAsta/NexoUI/main/dist/main.lua'))()
```

### Option 2 — Community example

```luau
loadstring(game:HttpGet('https://raw.githubusercontent.com/SirAsta/NexoUI/refs/heads/main/main_example.lua'))()
```

Then grab the `NexoUI` object returned and call `NexoUI:CreateWindow(...)`.

---

## 🚀 Quick Start

```luau
-- Load the library
local NexoUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/SirAsta/NexoUI/main/dist/main.lua"))()

-- Create a window
local Window = NexoUI:CreateWindow({
	Title = "MineName Hub",
	Author = "by you",
	Folder = "FolderName",          -- config save folder
	Icon = "solar:folder-2-bold-duotone",
	Theme = "Dark",                 -- or "Mellowsi"
	NewElements = true,
})

-- Create a tab
local Tab = Window:Tab({
	Title = "Main",
	Icon = "solar:home-2-bold",
	IconColor = Color3.fromHex("#10C550"),
	IconShape = "Square",
	Border = true,
})

-- Add a toggle (it saves its state under a Flag)
Tab:Toggle({
	Title = "My Toggle",
	Desc = "This is a toggle",
	Flag = "MyFlag",
	Default = true,
	Callback = function(value)
		print("Toggled to:", value)
	end,
})

-- Toggle the window open/closed
Window:Toggle()
```
---

## 🪟 Window Configuration

`NexoUI:CreateWindow(Config)` accepts the following options:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `Title` | `string` | — | Window title |
| `Author` | `string` | — | Author text in the title bar |
| `Folder` | `string` | — | Folder name used for config persistence |
| `Icon` | `string` | — | Icon asset name (e.g. `"solar:folder-2-bold-duotone"`) |
| `IconSize` | `number` | — | Size of the window icon |
| `Theme` | `string` | `"Dark"` | Theme ID (e.g. `"Dark"`, `"Mellowsi"`) |
| `NewElements` | `boolean` | `false` | Use the newer element design system |
| `Size` | `UDim2` | `(0,580,0,460)` | Initial window size |
| `Radius` | `number` | `3` | Window corner radius (square with small UI corners) |
| `ElementsRadius` | `number` | `3` | Corner radius of element cards |
| `Transparent` | `boolean` | `false` | Transparent window edges |
| `HideSearchBar` | `boolean` | `false` | Hide the search bar |
| `ScrollBarEnabled` | `boolean` | `false` | Show scrollbars |
| `SideBarWidth` | `number` | `200` | Sidebar / tab-list width |
| `Acrylic` | `boolean` | `false` | Enable acrylic (blur) background |
| `IgnoreAlerts` | `boolean` | `false` | Disable alert popups |
| `HidePanelBackground` | `boolean` | `false` | Hide panel background |
| `AutoScale` | `boolean` | `true` | Auto-scale the UI |
| `Resizable` | `boolean` | `true` | Allow resizing the window |
| `ToggleKey` | `Enum.KeyCode` | — | Key to open/close the window |
| `OpenButton` | `table` | — | Open/close floating button config |
| `Topbar` | `table` | — | Topbar config (`Height`, `ButtonsType = "Default"` / `"Mac"`) |

### OpenButton config

```luau
OpenButton = {
	Title = "Open My Hub UI",
	CornerRadius = UDim.new(1, 0),     -- fully rounded
	StrokeThickness = 3,                -- outline thickness
	Enabled = true,
	Draggable = true,
	OnlyMobile = false,
	Scale = 0.5,
	Color = ColorSequence.new(          -- gradient
		Color3.fromHex("#30FF6A"),
		Color3.fromHex("#e7ff2f")
	),
}
```

### Window methods

| Method | Description |
|--------|-------------|
| `Window:Tab({...})` | Create a tab |
| `Window:Section({...})` | Create a section directly on the window |
| `Window:Divider()` | Add a divider |
| `Window:Dialog({...})` | Open a dialog |
| `Window:Tag({...})` | Add a version/author tag to the titlebar |
| `Window:Open()` / `Window:Close()` | Open / close the window |
| `Window:Toggle()` | Toggle the window visibility |
| `Window:Destroy()` | Remove the window |
| `Window:SetTitle(text)` | Change the title |
| `Window:SetSize(size)` | Change the size |
| `Window:SetToggleKey(key)` | Change the toggle key |
| `Window:ToggleFullscreen()` | Toggle fullscreen |
| `Window:SetUIScale(v)` | Scale the UI |
| `Window:SetBackgroundImage(id)` | Set a background image |
| `Window:LockAll()` / `Window:UnlockAll()` | Lock / unlock all elements |
| `Window:EditOpenButton(cfg)` | Edit the open button |
| `Window:OnOpen(fn)` / `Window:OnClose(fn)` / `Window:OnDestroy(fn)` | Life-cycle callbacks |
| `Window:CreateTopbarButton(name, icon, cb)` | Add a custom topbar button |
| `Window.Topbar:Button({ ... })` | Add a topbar button (mac/default style) |
---

## 🌈 Theming

Set a theme globally, or load a custom one:

```luau
NexoUI:SetTheme("Mellowsi")        -- switch theme
NexoUI:AddTheme(MyCustomTheme)     -- register a custom theme
NexoUI:GetThemes()                 -- list available themes
NexoUI:GetCurrentTheme()           -- get the active theme
NexoUI:OnThemeChange(function(theme) end) -- listen to theme changes
```

Add a gradient background:

```luau
NexoUI:Gradient({
	["0"] = { Color = Color3.fromHex("#0f0c29"), Transparency = 0.5 },
	["1"] = { Color = Color3.fromHex("#24243e"), Transparency = 0.5 },
})
```

---

## 🧩 Elements

Elements are created on a `Tab`, `Section`, or `Group`. Every element accepts a config table and returns the element instance.

### Buttons

```luau
Tab:Button({
	Title = "Click me",
	Desc = "Description",
	Icon = "play",
	IconAlign = "Left",
	Color = Color3.fromHex("#a2ff30"),
	Callback = function()
		print("Clicked!")
	end,
})
```

### Toggle / Checkbox

```luau
Tab:Toggle({
	Title = "Toggle",
	Desc = "A toggle",
	Type = "Toggle",                  -- or "Checkbox"
	Value = true,                     -- initial value (use with Flag)
	Locked = false,
	Callback = function(value)
		print("Toggled:", value)
	end,
})
```

### Slider

```luau
Tab:Slider({
	Title = "Volume",
	IsTooltip = true,                 -- show the value while dragging
	IsTextbox = false,
	Step = 1,
	Width = 200,
	Value = { Min = 0, Max = 200, Default = 100 },
	Icons = { From = "sfsymbols:sunMinFill", To = "sfsymbols:sunMaxFill" },
	Callback = function(value) print(value) end,
})
```

### Keybind

```luau
Tab:Keybind({
	Title = "Keybind",
	Desc = "Opens the UI",
	Value = "G",
	Callback = function(key) print(key) end,
})
```

### Dropdown

```luau
Tab:Dropdown({
	Title = "Options",
	Multi = false,                    -- allow multiple selections
	Values = { "A", "B", "C" },
	-- Values = { { Title = "Copy", Icon = "copy", Desc = "...", Callback = function() end } }
	Value = "A",                      -- selected value
	Callback = function(value) print(value) end,
})
```

### Input

```luau
Tab:Input({
	Title = "Input",
	Desc = "Type here",
	Type = "Input",                   -- or "Textarea"
	InputIcon = "search",             -- optional leading icon
	Placeholder = "Enter text...",
	ClearOnFocus = true,
	Value = "hello",
	Callback = function(text) print(text) end,
})
```

### Colorpicker

```luau
Tab:Colorpicker({
	Title = "Color",
	Default = Color3.fromRGB(255, 0, 100),
	Callback = function(color) print(color) end,
})
```

### Other available elements

| Element | Description |
|---------|-------------|
| `Tab:Paragraph({...})` | A paragraph text block |
| `Tab:ProgressBar({...})` | An animated progress bar |
| `Tab:Section({...})` | A titled section (can contain sub-elements) |
| `Tab:Group({...})` | A group container for multiple elements |
| `Tab:HStack({...})` / `Tab:VStack({...})` | Horizontal / vertical layout containers |
| `Tab:Divider({...})` | A visual divider line |
| `Tab:Space({ Columns = n })` | Vertical spacing between elements |
| `Tab:Image({ Image = "...", AspectRatio = "16:9", Radius = 9 })` | An image |
| `Tab:Viewport({...})` | A 3D viewport |
| `Tab:Code({...})` | A code block |

### Tab methods

| Method | Description |
|--------|-------------|
| `Tab:Button(...)` | Add a button |
| `Tab:Toggle(...)` | Add a toggle / checkbox |
| `Tab:Slider(...)` | Add a slider |
| `Tab:Keybind(...)` | Add a keybind |
| `Tab:Dropdown(...)` | Add a dropdown |
| `Tab:Input(...)` | Add a text input |
| `Tab:Colorpicker(...)` | Add a colorpicker |
| `Tab:ProgressBar(...)` | Add a progress bar |
| `Tab:Section(...)` | Add a titled section |
| `Tab:Space(...)` | Add spacing |
| `Tab:LockAll()` / `Tab:UnlockAll()` | Lock / unlock a tab's elements |
---

## 📁 Configuration System (Flags)

Use `Flag` on any **stateful** element (toggle, slider, keybind, input, dropdown, colorpicker) so its value can be **saved and restored** via the window's config manager.

```luau
Tab:Toggle({
	Flag = "Door.Toggle",
	Callback = function(value)
		-- value can be loaded later
	end,
})

Tab:Slider({
	Flag = "Shark.Delay",
	Value = { Min = 0, Max = 200, Default = 100 },
})
```

> Each window's configs are identified by its unique `Folder`. From the UI you can save / load / delete configs, so all `Flag`-ed element values persist between sessions.

---

## 🔧 Building from Source

Requirements:

- [darklua](https://github.com/seaofvoices/darklua/releases) binary (v0.19.0+) on your `PATH`
- `node` for the build metadata (version / date / license header)

`package.json` already defines the build scripts:

```bash
# Production build -> dist/main.lua (entry: src/Init.lua)
npm run build

# Dev build of any file
npm run dev -- INPUT_FILE=main.client.lua
```

Or directly:

```bash
bash build/build.sh build     # -> dist/main.lua
bash build/build.sh dev main  # dev mode
```

The build combines a generated header (see `build/header.lua`) with a darklua-bundled version of `src/Init.lua` and all of its dependencies.

---

## 📁 Project Structure

```
.
├── build/                 # Build tooling (build.sh, darklua config, header)
├── dist/
│   └── main.lua           # Compiled single-file library (used by loadstring)
├── src/
│   ├── Init.lua           # Library entry point + public API
│   ├── modules/           # Core (Creator, icons, themes, etc.)
│   ├── components/        # Windowing, notifications, popups, key system
│   │   ├── ui/            # Low-level controls (Button, Toggle, Slider, Tag, ...)
│   │   └── window/        # Window, Tab, Section, Element, Dialog
│   └── elements/          # High-level library elements
├── main.client.lua        # Full in-depth example (Studio / script)
├── main2.client.lua       # Secondary example
├── main_example.lua       # Example entry used by loadstring
├── package.json
└── README.md
```

---

## 🙏 Credits

#### Icons (https://github.com/Footagesus/Icons)

- [Lucide-Icons](https://github.com/lucide-icons/lucide)
- [Craft Icons](https://www.figma.com/community/file/1415718327120418204)
- [Geist Icons](https://vercel.com/geist/icons)
- [Solar Icons](https://icones.js.org/collection/solar)
- [SF Symbols](https://sf-symbols-one.vercel.app/)

### Built with

- [darklua](https://github.com/seaofvoices/darklua) — Lua → Lua bundler / minifier

---

<div align="center">

**NexoUI** — made with ❤️ by **SirAsta** · [MIT License](LICENSE)

</div>
