# Local Cache and Storage Policy

> **Engineering policy, not legal advice.** Last updated: 2026-10-14. Based on the code under
> `app/src/main` as of this date. Re-check when a new storage API or SDK is added.

This document lists what LectureX keeps on the device, how long it stays, what is excluded from backup, and how it is
removed. It states only what the code does. Items marked "not found" were searched for and not present.

## 1. What is stored on the device

| Item | Where | Set by | Lifetime | Notes |
|---|---|---|---|---|
| Clerk session token | Clerk SDK storage (app private storage) | Clerk Android SDK | Until sign-out or token expiry | Managed by Clerk; excluded from backup (see section 3) |
| Current user id | Memory only (`CurrentUser`) | `data/CurrentUser.kt` | Until the app process ends or sign-out (`clear()`) | Not written to disk |
| Import camera capture (`capture.jpg`) | `cacheDir/import_capture/` (exposed to the camera app through `FileProvider`, cache-path `import_capture/`) | `ui/screens/ImportScreen.kt` | Overwritten by the next capture. The code does not delete it after use. Android may clear the app cache at any time | The image is the user's document photo; OCR runs on the device |
| Imported PDF working copy | `cacheDir` temporary file (`import*.pdf`) | `importer/OcrService.kt` | Deleted in a `finally` block after rendering, including on failure | Used for on-device OCR |
| Update check result | Not cached. Fetched when the user chooses "Check for Updates" | `data/AppUpdateChecker.kt` | Held only in the dialog state | No DataStore, SharedPreferences or file write found |
| Downloaded APK | Not stored by the app. The HTTPS link opens in the browser, which handles the download | `ui/components/AppUpdateDialog.kt` | Governed by the browser and the user's Downloads folder | Install is performed by the user |

Not found in `app/src/main`: DataStore, SharedPreferences (app code), Room or any other local database, `filesDir` writes,
external storage writes, `DownloadManager`, and any analytics or crash-report store.

Server-side data (timetables, requests, offers, releases) is held in Supabase, not on the device. Its retention is in
[DATA_RETENTION_AND_DELETION.md](DATA_RETENTION_AND_DELETION.md).

## 2. What is not cached

- Timetable, request and notification data is fetched from Supabase when a screen loads. The code in `data/` does not
  write these responses to disk.
- Update-check responses (`app_releases` rows) are not stored.

## 3. Backup and transfer exclusion

- `android:allowBackup="false"` in `AndroidManifest.xml`.
- `res/xml/backup_rules.xml` (full backup, Android 6 to 11) excludes all domains (`root`, `file`, `database`,
  `sharedpref`, `device_*`).
- `res/xml/data_extraction_rules.xml` (Android 12 and later) excludes all domains for both `cloud-backup` and
  `device-transfer`.
- Result: the session token and cached files are not included in cloud backup or device-to-device transfer. Signing in
  again is required on a new device.

## 4. How local data is removed

| Event | What is removed |
|---|---|
| Sign-out | The in-memory user id is cleared (`CurrentUser.clear()`). Ending the Clerk session is handled by the Clerk SDK; this review did not verify the sign-out path on a device |
| Uninstall | All app-private storage, including the Clerk session and the cache, is deleted by Android |
| Clear storage (Settings) | Same as uninstall for app-private data; the user must sign in again |
| Clear cache (Settings) | Removes `cacheDir` contents, including any leftover `capture.jpg` |
| Normal app use | `capture.jpg` is overwritten on the next capture. The temporary PDF is deleted after each OCR run |

The app does not offer an in-app "clear cache" control.

## 5. Things the user should know

- A photo of a timetable or notice may remain in the cache until the next capture or until the cache is cleared. Clear
  app storage on a shared device after importing.
- Removing data from the server is not done by clearing the device. See the deletion procedure in
  [DATA_RETENTION_AND_DELETION.md](DATA_RETENTION_AND_DELETION.md).
- Update checks contact Supabase only. The download itself goes through the browser to the HTTPS host named in the release
  row (GitHub Releases on the public repository `Zenithquonta/lecturex-releases`).
