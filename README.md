# US Southwest theater for Falcon BMS 4.38.2

The US Southwest add-on theater: the western United States and northern Mexico on a 2,048 km square, with 783 airfields,
generated buildings, real aerial imagery, night lighting, an objective network and five campaigns.

Free add-on, not for sale. Not affiliated with or endorsed by Benchmark Sims.

## Install, update, repair: one program

Download **[USSouthwest_Installer.exe](https://github.com/eastwoodtattoo/USSouthwest-Theater/releases/latest/download/USSouthwest_Installer.exe)** and run it with Falcon BMS closed.
It is not code-signed, so Windows SmartScreen may warn: "More info", then "Run anyway".

It finds your BMS folder (or choose it with **Browse...**) and then:

- **Not installed yet:** choose the ground textures and real weather, then **Install**. Everything is downloaded from this page,
  file by file, and every file is checked against its SHA-256 checksum before it is written. If the download is interrupted, run the
  program again: **Continue install** picks up where it stopped.
- **Installed:** **Update** downloads only the files that changed since your version. **Check files** compares every installed file
  with the published list (seconds); **Full check** reads every file and compares its checksum (slow from a hard disk; changes nothing).
  Anything damaged or missing is downloaded again.
- **Uninstall** removes the theater folder, its models and textures, its line in BMS's theater list and the real-weather program.
  Stock BMS files are never changed.

| | Standard | High resolution |
|---|---|---|
| Ground textures | Landsat satellite imagery, 15.6 m per pixel | adds NAIP aerial photography, 3.9 m per pixel |
| Download | about 42 GB | about 147 GB |
| On disk | about 61 GB | about 231 GB |

Both also need a copy of your own BMS `Data\Sounds` folder (the theater adds its spoken airfield names to that copy; no original BMS
audio is distributed). Everything else is the same in both: airfields, buildings, bridges, lights, night textures, campaigns.
The high-resolution ground can be added later with its tick box, then **Update**. Unticking it removes the high-resolution tiles
after a warning that asks you to confirm.

**Real weather** (optional, a tick box): a small program starts with Windows and waits; while BMS runs it downloads NOAA's free
forecast (about 1 MB per hour) and keeps the weather of the theater's missions current. It contacts NOAA and nothing else.

After installing: start Falcon BMS, choose **US Southwest** in the Theater menu, then restart BMS.

## Unattended use

```
USSouthwest_Installer.exe /silent [/bms="X:\your BMS folder"]
    /install [/hires] [/weather=on|off]      fresh install
    /check | /fullcheck | /update            check, or bring an install to the latest version
    /ground=16K | /ground=4K [/update]       high-resolution ground on or off
    /uninstall
    [/log=file]
```

Exit code 0 = nothing to do or done, 1 = stopped with a reason in the log, 2 = error, 3 = (check) an update or repair is waiting.

## What is in a release here

| File | What it is |
|---|---|
| `USSouthwest_Installer.exe` | the program (install, update, repair, uninstall) |
| `latest.json` | which version is the latest and where its files are |
| `USSouthwest-1.0.1.idx.gz`, `update-<version>.idx` | the file lists, with the SHA-256 of every file |
| `update-<version>-NNN.pak` | the files that changed in that version (files that did not change stay in the release that brought them) |

The data of version 1.0.1 is in the release `base-1.0.1`. The program reads only the parts of each data file it needs.
