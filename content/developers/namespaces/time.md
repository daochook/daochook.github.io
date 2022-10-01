---
title: "time"
---

The `time` namespace contains functions that offer more precise timing related information. Lua only offers two time related methods by default which don't offer much in regards to precision timing, or other useful time related info.

Functions exposed by this namespace are accessed via the prefix: `hook.time.`

### Functions

#### `clock`

Returns the current high-resolution clock information. _(Uses std::chrono::high\_resolution\_clock::now)_

```lua
table hook.time.clock();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(table)_ Table containing the high-resolution clock information. |

The returned table contains the following properties:

  - `s` _(number)_ - The number of seconds of the high-res clock.
  - `ms` _(number)_ - The number of milli-seconds of the high-res clock.
  - `micro` _(number)_ - The number of micro-seconds of the high-res clock.
  - `nano` _(number)_ - The number of nano-seconds of the high-res clock.

---

#### `query_performance_counter`, `qpc`

Returns a table containing the current performance counter information. _(Uses QueryPerformanceCounter)_

```lua
table hook.time.query_performance_counter();
table hook.time.qpc();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(table)_ Table containing the current performance counter information. |

The returned table contains the following properties:

  - `quad_part` _(number)_ - The performance counter quad part.
  - `high_part` _(number)_ - The performance counter high part.
  - `low_part` _(number)_ - The performance counter low part.
  - `q` _(number)_ - The performance counter quad part. _(Shorthand naming.)_
  - `h` _(number)_ - The performance counter high part. _(Shorthand naming.)_
  - `l` _(number)_ - The performance counter low part. _(Shorthand naming.)_

---

#### `query_performance_frequency`, `qpf`

Returns a table containing the current performance frequency information. _(Uses QueryPerformanceFrequency)_

```lua
table hook.time.query_performance_frequency();
table hook.time.qpf();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(table)_ Table containing the current performance frequency information. |

The returned table contains the following properties:

  - `quad_part` _(number)_ - The performance frequency quad part.
  - `high_part` _(number)_ - The performance frequency high part.
  - `low_part` _(number)_ - The performance frequency low part.
  - `q` _(number)_ - The performance frequency quad part. _(Shorthand naming.)_
  - `h` _(number)_ - The performance frequency high part. _(Shorthand naming.)_
  - `l` _(number)_ - The performance frequency low part. _(Shorthand naming.)_

---

#### `get_local_time`, `glt`

Returns a table containing the current local time. _(Uses GetLocalTime)_

```lua
table hook.time.get_local_time();
table hook.time.glt();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(table)_ Table containing the current local time information. |

The returned table contains the following properties:

  - `year` _(number)_ - The local time year value.
  - `month` _(number)_ - The local time month value.
  - `dayofweek` _(number)_ - The local time day of week value.
  - `day` _(number)_ - The local time day value.
  - `hour` _(number)_ - The local time hour value.
  - `minute` _(number)_ - The local time minute value.
  - `second` _(number)_ - The local time second value.
  - `ms` _(number)_ - The local time millisecond value.
  - `y` _(number)_ - The local time year value.
  - `m` _(number)_ - The local time month value.
  - `wd` _(number)_ - The local time day of week value.
  - `d` _(number)_ - The local time day value.
  - `hh` _(number)_ - The local time hour value.
  - `mm` _(number)_ - The local time minute value.
  - `ss` _(number)_ - The local time second value.

---

#### `get_system_time`, `gst`

Returns a table containing the current system time. _(Uses GetSystemTime)_

```lua
table hook.time.get_system_time();
table hook.time.gst();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(table)_ Table containing the current system time information. |

The returned table contains the following properties:

  - `year` _(number)_ - The system time year value.
  - `month` _(number)_ - The system time month value.
  - `dayofweek` _(number)_ - The system time day of week value.
  - `day` _(number)_ - The system time day value.
  - `hour` _(number)_ - The system time hour value.
  - `minute` _(number)_ - The system time minute value.
  - `second` _(number)_ - The system time second value.
  - `ms` _(number)_ - The system time millisecond value.
  - `y` _(number)_ - The system time year value.
  - `m` _(number)_ - The system time month value.
  - `wd` _(number)_ - The system time day of week value.
  - `d` _(number)_ - The system time day value.
  - `hh` _(number)_ - The system time hour value.
  - `mm` _(number)_ - The system time minute value.
  - `ss` _(number)_ - The system time second value.

---

#### `get_tick`, `tick`

Returns the current system tick count. _(Uses GetTickCount)_

```lua
table hook.time.get_tick();
table hook.time.tick();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The current system tick count. |

---

#### `get_tick64`, `tick64`

Returns the current system tick count. _(Uses GitTickCount64)_

```lua
table hook.time.get_tick64();
table hook.time.tick64();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The current system tick count. |

---
