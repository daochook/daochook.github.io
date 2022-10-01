---
title: "imgui"
---

The `imgui` namespace contains functions that are used to interact with the ImGui library. **daochook** offers a [nearly] full implementation of ImGui, adjusted to work nicer with Lua.

Due to how many functions are within ImGui, this documentation may remain 'lacking' for a bit of time. However, some bits of information will be explained to help understand the changes made to the functions in order to make use of them in your addons.

Functions exposed by this namespace are accessed via the prefix: `gui.`

{{% notice tip %}}
**daochook** includes a helper lib for addons that should be used when your addon will make use of imgui.\
\
`require 'imgui';`
{{% /notice %}}

_When using the `imgui` addon lib, you can instead directly access the ImGui functions via the `imgui.` namespace._

{{% notice info %}}
**daochook** implements and makes use of ImGui v1.88. You can find info about it here:\
https://github.com/ocornut/imgui\
https://github.com/ocornut/imgui/tree/v1.88
{{% /notice %}}

### ImGui Function Changes

The following changes are made to all ImGui functions that are exposed.

#### Parameter Changes

  - Any function that takes an `ImVec2(..)` parameter is instead, replaced with a table holding two numbers.
  - Any function that takes an `ImVec3(..)` parameter is instead, replaced with a table holding three numbers.
  - Any function that takes a `bool*` parameter is instead, replaced with a table holding a boolean property.
  - Any function that accepts `...` is not implemented, use the non-vararg variant of the function instead.
  - Any function that accepts `va_list` is not implemented, use the non-vararg variant of the function instead.

#### Return Changes

  - Any function that returns `ImVec2(..)` will return two values instead.
  - Any function that returns `ImVec3(..)` will return three values instead.

### Examples of Changes

Some examples of these changes are as follows:

```lua
-- Original:
-- ImVec2 GetCursorScreenPos(void);

-- Changed:
local x, y = imgui.GetCursorScreenPos();
```

```lua
-- Original:
-- void PushStyleColor(ImGuiCol idx, const ImVec4& col);

-- Changed:
imgui.PushStyleColor(0, { 1.0, 1.0, 1.0, 1.0, });
```

```lua
-- Original:
-- ImU32 GetColorU32(const ImVec4& col);

-- Changed:
local color = imgui.GetColorU32({ 1.0, 1.0, 1.0, 1.0, });
```

```lua
-- Original:
-- bool Button(const char* label, const ImVec2& size = ImVec2(0, 0));

-- Changed:
if (imgui.Button('Derp')) then print('Derp clicked.'); end
if (imgui.Button('Derp', { 25.0, 25.0, })) then print('Derp clicked.'); end
```

```lua
-- Original:
-- bool Checkbox(const char* label, bool* v);

-- Changed:
local window = T{
    is_checked = T{ true, },
};
imgui.Checkbox('Derp', window.is_checked);
```
