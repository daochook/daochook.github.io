---
title: "Running daochook"
weight: 2
---

### Launching daochook

**daochook** expects a boot configuration file to be passed to its launcher when running, such as:

```
daochook.exe atom0s.ini
```

When the launcher starts, it will take the given file name and locate it within the boot configuration directory automatically.\
The path to the **daochook** boot configuration directory is: `<Path To daochook>\config\boot\`

_Be sure to read the [configurations documentation](/usage/configurations/) page for more information on how to configure **daochook**._

### Playing On Private Servers

**daochook** is developed and designed mainly for private server usage. It is very easy to adjust your configuration file to work with private servers that run using DOL.

Inside of your configuration file, the main setting you need to set is:

```ini
[daochook.patches]
disable_encryption = 1
```

_This will patch out the encryption of the client which DOL requires to be disabled._

### Playing On Retail Servers

**daochook** is developed and designed mainly for private server usage, however, it should work fine on retail servers as well.

Inside of your configuration file, the main setting you need to set is:

```ini
[daochook.patches]
disable_encryption = 0
```

You should then properly fill out the server information you are trying to log into in order to properly connect to the retail servers using **daochook**'s injector.

### Retail Server Address Information

Below is a table of the current retail server list. _(Updated as of 10.02.2022)_

| Test (PTR) Servers |
| --- |

| Server Name | IP Address | Port | Id |
| --- | --- | --- | --- |
| Hector        | 107.23.114.74     | 10622 | 40    |
| Pendragon     | 107.23.114.74     | 10622 | 5     |

| Normal (All Ywain) Servers |
| --- |

| Server Name | IP Address | Port | Id |
| --- | --- | --- | --- |
| Ywain1        | 107.23.173.143    | 10622 | 41    |
| Ywain2        | 107.23.173.143    | 10622 | 49    |
| Ywain3        | 107.23.173.143    | 10622 | 50    |
| Ywain4        | 107.23.173.143    | 10622 | 51    |
| Ywain5        | 107.23.173.143    | 10622 | 52    |
| Ywain6        | 107.23.173.143    | 10622 | 53    |
| Ywain7        | 107.23.173.143    | 10622 | 54    |
| Ywain8        | 107.23.173.143    | 10622 | 55    |
| Ywain9        | 107.23.173.143    | 10622 | 56    |
| Ywain10       | 107.23.173.143    | 10622 | 57    |

| Alternate Ruleset Servers |
| --- |

| Server Name | IP Address | Port | Id |
| --- | --- | --- | --- |
| Gaheris       | 107.21.60.95      | 10622 | 23    |

| Archived Servers |
| --- |

| Server Name | IP Address | Port | Id |
| --- | --- | --- | --- |
| Akatsuki      | 107.23.34.34      | 10622 | 35    |
| Avalon        | 107.23.214.48     | 10622 | 84    |
| Bedevere      | 107.23.34.34      | 10622 | 16    |
| Bors          | 107.23.18.149     | 10622 | 19    |
| Broceliande   | 107.23.200.161    | 10622 | 80    |
| Camlann       | 107.23.154.120    | 10622 | 89    |
| Carnac        | 107.23.200.161    | 10622 | 83    |
| Cumbria       | 107.23.187.235    | 10622 | 93    |
| Dartmoor      | 107.23.214.48     | 10622 | 88    |
| Deira         | 107.23.162.153    | 10622 | 92    |
| Ector         | 107.23.210.32     | 10622 | 34    |
| Excalibur     | 107.23.173.127    | 10622 | 90    |
| Galahad       | 107.23.34.34      | 10622 | 10    |
| Gareth        | 107.23.210.32     | 10622 | 33    |
| Gawaine       | 107.23.18.149     | 10622 | 18    |
| Glastonbury   | 107.23.78.91      | 10622 | 94    |
| Guinevere     | 107.23.18.149     | 10622 | 15    |
| Igraine       | 107.23.34.34      | 10622 | 28    |
| Iseult        | 107.23.34.34      | 10622 | 20    |
| Kay           | 107.23.34.34      | 10622 | 26    |
| Lamorak       | 107.23.210.32     | 10622 | 32    |
| Lancelot      | 107.23.34.34      | 10622 | 11    |
| Logres        | 107.23.214.48     | 10622 | 87    |
| Lyonesse      | 107.23.214.48     | 10622 | 85    |
| Merlin        | 107.23.18.149     | 10622 | 14    |
| Mordred       | 107.23.134.9      | 10622 | 31    |
| Morgan        | 107.23.34.34      | 10622 | 17    |
| Nimue         | 107.23.18.149     | 10622 | 22    |
| Orance        | 107.23.200.161    | 10622 | 82    |
| Palomides     | 107.23.18.149     | 10622 | 13    |
| Pellinor      | 107.23.34.34      | 10622 | 21    |
| Percival      | 107.23.18.149     | 10622 | 12    |
| Prydwen       | 107.23.173.127    | 10622 | 91    |
| Salisbury     | 107.23.78.91      | 10622 | 95    |
| Stonehenge    | 107.23.214.48     | 10622 | 86    |
| Tristan       | 107.23.34.34      | 10622 | 27    |
| Ys            | 107.23.200.161    | 10622 | 81    |