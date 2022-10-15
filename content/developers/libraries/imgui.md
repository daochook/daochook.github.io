---
title: "imgui"
---

The `imgui` library is used to allow addons to easily interact with the ImGui implementation within **daochook**. This library forwards the needed enumerations and flag definitions that are passed to the various ImGui function calls. This library also contains a few helper functions to do a few things with ImGui easier.

This library also forwards the implemented global table `gui` to `imgui` to make easier usage of things and to better align to the C++ style code.

### Using The Library

```lua
local imgui = require 'imgui';
```

### Functions

#### `col32`

Converts the given ARGB color values into a 32bit color.

```lua
number imgui.col32(a, r, g, b);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `a`   | _number_ | The alpha color value. |
| `r`   | _number_ | The red color value. |
| `g`   | _number_ | The green color value. |
| `b`   | _number_ | The blue color value. |

| Returns |
| --- |
| _(number)_ The converted 32bit color value. |

---

#### `ShowHelp`

Displays a helper tag `(?)` that displays the given text as a tooltip when hovered.

```lua
imgui.ShowHelp(text, same_line);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `text`        | _string_  | The tooltip text to display when hovering. |
| `same_line`   | _boolean_ | `[Optional]` Flag that states if the helper tag is displayed on the same line as the previous drawn element. _(Default is true.)_ |

| Returns |
| --- |
| _None._ |

---

#### `DisplayPopup`

Displays a modal popup _(similar to a message box)_ with configurable buttons and results.

```lua
number imgui.DisplayPopup(title, name, cb, buttons);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `title`       | _string_      | The title to display on the popup. |
| `name`        | _string_      | The internal ImGui hashtag name of the popup. |
| `callback`    | _function_    | The contents callback invoked to allow custom popup content rendering. |
| `buttons`     | _number_      | The button flag value used to determine which popup type to display. |

| Returns |
| --- |
| _number_ The PopupResult value. |

Valid button flags are:

  - `PopupButtonsOk` - 0
  - `PopupButtonsOkCancel` - 1
  - `PopupButtonsYesNo` - 2
  - `PopupButtonsYesNoCancel` - 3

Valid popup return values are:

  - `PopupResultNone` - 0
  - `PopupResultOk` - 1
  - `PopupResultCancel` - 2
  - `PopupResultYes` - 3
  - `PopupResultNo` - 4

---
