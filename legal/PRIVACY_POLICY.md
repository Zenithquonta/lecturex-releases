# Privacy Policy

> **TEMPLATE requiring review by qualified counsel.** Not legal advice. Effective date: `[EFFECTIVE_DATE]`. Last updated: 2026-10-14.
> Technical inventory this is drawn from: docs/PRIVACY.md (kept as the engineering description; this
> document is the user-facing notice and takes precedence on user rights).

**Who we are.** `[OPERATOR_LEGAL_NAME]`, `[OPERATOR_ADDRESS]` ("we"), operates LectureX, an Android app for managing
university timetables on behalf of `[INSTITUTION_NAME]` where applicable. Contact: `[CONTACT_EMAIL]`.
India grievance officer: `[GRIEVANCE_OFFICER]`.

## 1. Data we process

| Category | Examples | Source | Purpose | Stored in |
|---|---|---|---|---|
| Account | Name, email, role, account status, rejection reason | You / your administrator | Sign-in, authorisation, approval workflow | Clerk (email, password hash), Supabase `profiles` |
| Academic profile | Department (faculty), division and batch (students), faculty initials | You / administrator | Show the right timetable | Supabase `faculty`, `students` |
| Timetable and academic records | Lectures, rooms, exam schedule, holidays, course policies, teaching progress | You / administrator / approved imports | The service itself | Supabase |
| Exchange and unavailability requests | Reasons (free text), leave/duty category, notes up to 300 characters | You | Substitution, swap and planning workflows | Supabase |
| Imported documents | Draft content extracted from files you pick; file name (up to 200 chars); SHA-256 checksum | You | Review and publish schedules | Supabase `schedule_imports` |
| Substitution offers | Which eligible faculty were invited to cover a lecture, their priority, and their response (pending, accepted, declined, selected, cancelled) | Requester, system | Let one lecture be offered to several faculty and assign a single cover | Supabase `substitution_offers` |
| Update check | Your installed version code and the published release record (version, notes, download link). Only your signed-in session is sent, as for any other request | App, when you choose "Check for Updates" | Tell you a newer version exists | Read from Supabase `app_releases`; nothing is stored on the device |
| Notifications | Titles and messages about timetable changes | System | Inform affected users | Supabase `notifications` |
| Session data | Session token | Clerk SDK | Keep you signed in | On device (Clerk SDK storage) |

The selected file itself is processed **on your device** (ML Kit OCR / DOCX parsing) and is not uploaded. We do not
collect location, contacts, photos library, advertising ID, device identifiers, biometrics or usage analytics, and the app
contains no analytics, advertising or crash-reporting SDK (verified against the Gradle dependency list and manifest,
which requests only `INTERNET`). Free-text fields and document content could contain information you choose to type;
please avoid sensitive data not needed for scheduling.

We limit collection to the account, academic and scheduling data needed for the purposes in the table. Before adding a
field or SDK, the operator should document its purpose, whether it is necessary, who receives it, and how long it is kept.
The current third-party SDK inventory and outstanding provider checks are in
[DATA_PROCESSING_AND_SUBPROCESSORS.md](DATA_PROCESSING_AND_SUBPROCESSORS.md).

## 2. Legal bases and consent

- **GDPR (if applicable):** performance of a contract or the controller's legitimate interests in running timetabling
  (Art. 6(1)(b)/(f)); consent only where we say so. We do not knowingly process special-category data.
- **India DPDP Act 2023:** processing for the purposes you provide data for (consent, s.6) and, for an institution,
  certain legitimate uses (s.7). Notice contents follow s.5. Data of persons under 18 requires verifiable parental
  consent (s.9); the app has **no age gate today** (Planned), so the deploying institution must confirm that all users are
  adults or arrange consent.
- **CCPA/CPRA (California):** we do not sell or share personal information for cross-context advertising and use none for
  profiling. Categories collected are identifiers and professional/education information.
- **FERPA (US):** timetable and enrolment links can be education records when held for a US institution. The institution
  should treat the operator as a "school official" under a written agreement and control disclosure. FERPA is the
  institution's obligation; we do not certify it.
- **COPPA:** the service is not directed to children under 13 and we do not knowingly collect their data.

## 3. Who sees your data

Visibility is enforced by the database (row-level security): students see their own division; faculty see divisions they
teach plus requests they are party to; coordinators see requests for their divisions; administrators see all accounts and
timetables. Pending or rejected accounts see only their own profile.

**Substitution offers.** When a lecture is offered to several faculty, the requester, each faculty member invited to that
offer, the coordinator of the division that owns the lecture, and administrators can see the offer group. Invited faculty
can therefore see which other faculty were invited to the same lecture and their responses. Only the single selected cover
is written to the lecture timetable. Offer records are removed when the request they belong to is removed.
`[Counsel / product owner to confirm that invitees may see each other.]`

We do not sell data. We share it only with the processors in
[DATA_PROCESSING_AND_SUBPROCESSORS.md](DATA_PROCESSING_AND_SUBPROCESSORS.md): Clerk and Supabase, which hold your account
and app data, and GitHub, which hosts the app's installation file. GitHub receives no account or app data from LectureX.
It receives only the ordinary request your browser makes when you choose to download an update.

## 4. International transfers

Clerk, Supabase and GitHub may process data outside your country. Supabase region: `[SUPABASE_REGION]` (not recorded in
this repository). Transfers rely on `[GDPR: SCCs / adequacy; DPDP: s.16 permitted-country rules - counsel to confirm]`.

## 5. Retention

See [DATA_RETENTION_AND_DELETION.md](DATA_RETENTION_AND_DELETION.md). Currently records persist until deleted; no
automatic expiry exists.

## 6. Your rights

Depending on law: access, correction, erasure, restriction, portability, objection, withdrawal of consent, nomination
(DPDP s.14), grievance redress (DPDP s.13), and under CCPA the rights to know, delete, correct and non-discrimination.
Contact `[CONTACT_EMAIL]`; we aim to respond within 30 days (`[confirm statutory period]`). **Current limitation:** there is
no self-service account deletion or data export in the app; requests are handled manually by an administrator in both
Clerk and Supabase. Complaints may go to your data-protection authority or, in India, the Data Protection Board.

## 7. Security

TLS in transit (cleartext disabled), database-enforced access control, secrets kept server-side, Android backup disabled.
Updates are installed manually from a download link. The app does not install anything by itself, and a new version
installs over the old one only when it is signed with the same key, so your data is kept. Install only the download link
offered by the app or by your administrator.
Known limitations (no MFA, no release hardening yet) are listed in docs/SECURITY.md. No system is
perfectly secure. Breach notification will follow applicable law (`[72 hours under GDPR; CERT-In and DPDP rules in India]`).

## 8. Children

Not directed at children. The app has no age gate or parental-consent flow. The deploying institution must establish
eligibility and any required parent or guardian consent before giving a minor access. If you believe a child's data was
provided without the required consent, contact `[CONTACT_EMAIL]` to request review and deletion.

## 9. Changes

We will post changes here and update the effective date; material changes will be notified in-app (Planned).

## 10. Cookies, forms and email

The native Android app does not set browser cookies or use advertising or analytics trackers. When you choose to download
an update, the app opens the download link in your browser; cookies or tracking, if any, are then set by that browser
and the download host, not by the app. It therefore has no cookie
banner today. If a website, web view or non-essential tracking is introduced, publish an updated cookie notice and offer
the required consent choice before enabling that tracking; see [COOKIE_AND_TRACKING.md](COOKIE_AND_TRACKING.md).

Account registration and academic request forms collect the fields described in section 1. A deploying operator should
show this notice at the point of collection and obtain any consent required for a new purpose before collecting that data.
The app currently sends no marketing email. Clerk sends account verification messages; timetable notifications appear
inside the app. If optional marketing email is introduced, provide an unsubscribe link and honor opt-out requests.
