# Restora

Recover deleted files on NTFS drives. Scans the disk through the MFT and shows deleted files with recovery chances — pick what to restore.

**Download:** [restora.exe (latest release)](https://github.com/on1felix/Restora-exe/releases/latest/download/restora.exe)
No installation needed — single portable `.exe`. Windows 10/11, 64-bit.

## Features

- **MFT scan** — walks the disk's Master File Table directly and finds deleted file records, including name, original path, size and timestamps.
- **Recycle Bin scan** — also reads `$Recycle.Bin` (`$I` metadata files) to recover files deleted through the Recycle Bin.
- **Recovery chance score** — every file gets a recoverability estimate based on whether its clusters were overwritten (via the volume bitmap), so you know what's worth restoring.
- **Search and filters** — find files by name, filter by type (documents, images, video, audio, archives), show only recoverable, only recent, or above a minimum size; sortable results.
- **File details panel** — MFT reference, resident/non-resident data, compression and sparse flags, dates, exact allocation state.
- **One-click recovery** — select files, choose a target folder, Restora carves the data runs back onto disk. Restores to a *different* drive to avoid overwriting other deleted data.
- **Drive overview** — lists all drives with filesystem, total/free space, NTFS and journal status, SSD + TRIM detection (TRIM usually means unrecoverable).
- **Admin elevation** — raw disk access needs administrator rights; the app restarts itself elevated on request.
- **Live progress** — scan progress with records processed, files found and current phase; scan and recovery can be cancelled anytime.
- **Auto-update** — checks GitHub Releases on start, downloads and applies the new version in one click.
- **Statistics** — total found, recoverable count and size, files deleted in the last 24h, breakdown by file type.

## How to use

1. Run `restora.exe` (grant admin rights when asked — required to read the raw disk).
2. Pick a drive on the Drives page.
3. Wait for the scan to finish.
4. Search or filter the results, select files, click Recover and choose a folder **on another drive**.

## Important notes

- Act fast: the longer you use the disk after deletion, the higher the chance the data is overwritten.
- Never recover files onto the same drive you scan — it destroys other deleted files.
- Files on SSDs with TRIM enabled are usually unrecoverable — the drive wipes deleted blocks itself.
- Some antiviruses may flag the unsigned `.exe`. The code is closed for security reasons, but the download comes only from official GitHub Releases.

## Tech

Tauri 2 (Rust) + React + TypeScript. Raw volume access via Windows API, manual NTFS record parsing (fixups, attributes, data runs).

---

By [on1felix](https://github.com/on1felix) & squeezebtw. Free, no ads, no telemetry.
Questions and false-positive reports: Telegram [@On1Felix](https://t.me/On1Felix).
