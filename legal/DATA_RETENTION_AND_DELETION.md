# Data Retention and Deletion

> Last updated: 2026-10-14 (substitution offers, release records, capture cache).

> **TEMPLATE requiring review by qualified counsel.** Not legal advice. Periods marked `[proposed]` are suggestions,
> not current behaviour. Reconciles the "Retention and deletion" section of docs/PRIVACY.md.

## Current behaviour (as built)

Records persist until deleted. No automatic expiry or purge job exists. There is no self-service account deletion and no
data export.

| Data | Location | Current retention | Proposed schedule `[proposed]` |
|---|---|---|---|
| Identity (email, password hash) | Clerk | Until Clerk user deleted | Delete on account closure |
| Profile, faculty/student rows | Supabase | Until deleted; `ON DELETE CASCADE` from `profiles` removes `faculty`, `students`, `notifications` | Delete within 30 days of closure |
| Timetable, changes, exams, calendar | Supabase | Indefinite | Institutional records: per institution policy (e.g. 7 years) |
| Swap requests (reasons, notes) | Supabase | Indefinite | 2 years after term end |
| Substitution offers (invited faculty, priority, response) | Supabase `substitution_offers` | Indefinite; removed when the parent request is deleted (`ON DELETE CASCADE`) | Same as swap requests: 2 years after term end |
| Published release records (`app_releases`) | Supabase | Indefinite. Contains no personal data | Keep published history for support; never reuse a version code |
| Unavailability (category, note) | Supabase | Indefinite | 1 year after term end |
| Import drafts and results (`schedule_imports`) | Supabase | Indefinite | Purge drafts 90 days after approval/rejection |
| Notifications | Supabase | Indefinite | 1 year |
| Session token | Device (Clerk SDK) | Until sign-out/expiry; excluded from Android backup | unchanged |
| Backups of Supabase | Supabase platform | Provider schedule (not configured here) | Confirm in processor DPA |

Local files: picked/captured documents are processed in memory or in a temporary file; the app deletes temporary PDF
render files (instrumented test `SoftwareVerificationTest`). A camera capture of a document is written to the app cache
(`import_capture/capture.jpg`) and is overwritten by the next capture; the code does not delete it after use. See
[CACHE_POLICY.md](CACHE_POLICY.md). Application backup is disabled (`allowBackup=false`,
extraction rules exclude all domains).

## Manual deletion procedure (until automated)

1. Verify the requester's identity through their registered email.
2. In Supabase delete or anonymise the `profiles` row (cascades to `faculty`, `students`, `notifications`). Note that
   `timetable`, `swap_requests`, `timetable_changes`, `schedule_imports.uploaded_by` and `reviewed_by` columns reference
   people without cascade, so deletion may require reassigning or nulling them; the foreign keys will block a naive
   delete. Planned: a tested `delete_account` procedure.
3. Delete the Clerk user (Clerk dashboard/Backend API). Deleting only one side leaves an orphan.
4. Record the action and response date; confirm within the statutory period (`[30 days GDPR / DPDP: reasonable time]`).

## Rights handling

| Right | Law | Status |
|---|---|---|
| Access / export | GDPR Art. 15/20; DPDP s.11; CCPA | Manual, no export tool (Planned) |
| Correction | GDPR Art. 16; DPDP s.12; CCPA | Admin edit (limited UI) |
| Erasure | GDPR Art. 17; DPDP s.12; CCPA | Manual procedure above |
| Withdraw consent | DPDP s.6(4) | By account closure request |
| Student requests for education records | FERPA | Route to `[INSTITUTION_NAME]` registrar |

Academic records that the Institution must retain by law may be kept despite an erasure request; counsel to define.

Deleting a person also affects their substitution offers: when the person's profile is removed, offers that reference
them (`substitution_offers.faculty_id`) are not cascaded automatically. Reassign or remove them in the same manual step.
