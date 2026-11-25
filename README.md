# US Southwest theater for Falcon BMS 4.38.2 - updater and updates

This repository hosts the **updater** of the US Southwest add-on theater and the files it downloads.
The theater itself (a 140 GB download) is distributed by torrent:

```
magnet:?xt=urn:btih:5701cbb1351c4ced4e656c94296e1dda2637560d&dn=USSouthwest_Installer_1.0.1&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Fopen.stealth.si%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.com%3A1337%2Fannounce&tr=udp%3A%2F%2Fexplodie.org%3A6969%2Fannounce
```

Free add-on, not for sale. Not affiliated with or endorsed by Benchmark Sims.

## Updating or checking an installed theater

1. Download **[USSouthwest_Updater.exe](https://github.com/eastwoodtattoo/USSouthwest-Theater/releases/latest/download/USSouthwest_Updater.exe)**.
   It is not code-signed, so Windows SmartScreen may warn: "More info", then "Run anyway".
2. Close Falcon BMS.
3. Run the updater. It finds your BMS folder, shows the installed and the latest version, and offers:
   - **Check files** - compares every installed file with the published list (size and date; takes seconds).
   - **Full check** - reads every installed file and compares its SHA-256 checksum (about 225 GB; takes a long time from a hard disk). Changes nothing.
   - **Update** - downloads only the files that changed and writes them. Every file is checked against its checksum before it replaces the installed one.

The updater only works on a theater that was installed with `Setup.exe` from the full download.
It never changes a stock BMS file. Setup's Uninstall still removes everything after updates.

If a check finds damaged files that are not part of an update, the updater can restore them from your original
download: button **Use my download...**, then choose the folder with the `USSouthwest-0xx.pak` files.

Unattended use: `USSouthwest_Updater.exe /silent [/bms="X:\your BMS folder"] [/check | /fullcheck | /update] [/data=<folder with the .pak files>] [/log=file]`
(exit code 0 = nothing to do or done, 1 = stopped with a reason in the log, 3 = an update or repair is waiting).

## What is in a release here

| File | What it is |
|---|---|
| `USSouthwest_Updater.exe` | the updater |
| `latest.json` | which version is the latest |
| `USSouthwest-1.0.1.idx.gz` | the file list of the full package, with the SHA-256 of every file |
| `update-<version>.idx`, `update-<version>-NNN.pak` | the files that differ from version 1.0.1 (every update is cumulative) |
