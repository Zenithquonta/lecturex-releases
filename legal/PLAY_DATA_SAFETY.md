# Google Play Data safety - draft answers

> **TEMPLATE requiring review.** Derived from `AndroidManifest.xml`, `app/build.gradle.kts` and the data inventory.
> The owner is responsible for the accuracy of the submitted form. Not yet submitted; no Play listing exists.
> Last updated: 2026-10-14 (substitution offers and the manual update check added).

## Declared facts

- Permissions: `INTERNET` only (no camera/storage/location permission). Photos are captured by handing off to the system
  camera (`ActivityResultContracts.TakePicture`) and documents are chosen with the system picker (`OpenDocument`), so no
  runtime permission is requested.
- Backup: `allowBackup=false`; cleartext traffic disabled.
- No ads, no analytics SDK, no crash SDK.

## Form answers

| Question | Answer |
|---|---|
| Does the app collect or share required user data types? | Yes (collects); no sharing for advertising |
| Is all data encrypted in transit? | Yes (HTTPS only) |
| Can users request data deletion? | **Not yet in-app.** Select "Yes" only once a request channel is published (see [retention](DATA_RETENTION_AND_DELETION.md)); a deletion-request web URL is required by Play for apps with accounts (Planned) |
| Data shared with third parties | Declare Clerk and Supabase as **service providers** (processing on the developer's behalf is not "sharing") |

| Data type | Collected | Shared | Purpose | Optional | Notes |
|---|---|---|---|---|---|
| Name | Yes | No | App functionality, account management | No | `profiles.name` |
| Email address | Yes | No | App functionality, account management | No | Clerk + mirrored to `profiles.email` |
| User IDs | Yes | No | App functionality | No | Clerk user id, profile uuid |
| Password | Handled by Clerk (not stored by the app backend) | No | Account management | No | Declare via Clerk |
| Other user-generated content | Yes | No | App functionality | Yes | Request reasons, notes, imported schedule drafts |
| Other info: substitution offers | Yes | No | App functionality | Yes | Invited faculty, priority and response per lecture cover request (`substitution_offers`) |
| Other info (role, department, division, batch) | Yes | No | App functionality | No | |
| Calendar/schedule data | Yes | No | App functionality | No | Academic timetable held on server, not the device calendar |
| Photos / files | **Not collected** | - | - | - | Processed on device; only extracted draft text and checksum are sent |
| Location, contacts, financial, health, messages, audio, web history, device IDs, app activity/analytics | Not collected | - | - | - | |

## Other Play requirements (status)

| Item | Status |
|---|---|
| Privacy policy URL | Draft in [PRIVACY_POLICY.md](PRIVACY_POLICY.md); needs hosting - Planned |
| Target API level | targetSdk 37 (verify against Play's requirement at submission) |
| App signing / AAB | Not configured; see RELEASE_AND_DEPLOYMENT |
| Account deletion URL and in-app path | Not implemented - blocker for publication |
| Test credentials for reviewers | Not prepared |
| Content rating questionnaire, target audience (not children) | Not done |
| Manual APK update outside Google Play | **Policy question for counsel / owner.** The "Check for Updates" action opens a direct APK download link (GitHub Release on `Zenithquonta/lecturex-releases`, 1.1.0 published) and the user installs it outside Play. Google Play's device and distribution policies restrict in-app or out-of-Play updates for Play-distributed apps. Confirm eligibility before publishing to Play, or keep this path for direct-install builds only |
