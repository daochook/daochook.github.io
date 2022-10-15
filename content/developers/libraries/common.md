---
title: "common"
---

The `common` library is a general purpose library used to pull in and require commonly used librarys in a central single file. This library can be used to pull in general purpose libraries within a single require to avoid the need to manually include individual additional libraries over and over in addons.

The common library will automatically include the following other libraries:

  - `sugar`
  - `switch`
  - `try`

### Using The Library

```lua
require 'common';
```

### Functions

_This library file does not define any new functions itself._
