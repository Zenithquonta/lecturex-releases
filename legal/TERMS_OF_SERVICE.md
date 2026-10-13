# Terms of Service

> **TEMPLATE requiring review by qualified counsel.** Not legal advice. Effective date: `[EFFECTIVE_DATE]`. Last updated: 2026-10-14.

These terms govern use of LectureX provided by `[OPERATOR_LEGAL_NAME]` ("we") to members of `[INSTITUTION_NAME]`
("Institution"). If you use LectureX you agree to them; if an Institution contract conflicts, the contract prevails for
that Institution.

LectureX is a student project developed for non-commercial academic use. It is not an official Institution system. The
Institution's official timetable, its policies and the decisions of its coordinators and administrators prevail over
anything shown in the app.

1. **Eligibility and accounts.** You must be authorised by the Institution and old enough to contract in your
   jurisdiction (under 18 in India requires a parent or guardian; see Privacy Policy s.2). You register as Student,
   Faculty or Coordinator and must wait for administrator approval; Administrator accounts are created only by an
   administrator. Your selected role does not grant permissions; the system checks your actual role. Keep credentials
   confidential; use a unique password of at least 15 characters.
2. **The service.** LectureX displays timetables and routes substitution and swap requests through faculty acceptance and
   coordinator approval, and offers import, calendar, planning and progress tools. Timetable changes take effect only on
   final approval. Substitution offers are described in section "Substitution offers" below.
3. **Imports are your responsibility.** OCR and parsing can be wrong. Imported content must be reviewed before
   submission and is published only after approval by an authorised reviewer. We do not guarantee accuracy or
   completeness; the Institution's official timetable prevails.
4. **Acceptable use.** You agree to the [Acceptable Use Policy](ACCEPTABLE_USE_POLICY.md).
5. **Your content.** You keep ownership of content you submit (request reasons, imported schedules). You grant us and the
   Institution a limited licence to host and display it to provide the service.
6. **Privacy.** See the [Privacy Policy](PRIVACY_POLICY.md).
7. **Availability and changes.** The service is provided as-is during pre-release; we may change, suspend or discontinue
   features. Backend changes may be deployed in stages. We do not guarantee continuous availability of the backend, of
   the update check, or of the download host described in "Distribution of the Android app" below.
8. **Open-source software.** The application source is under the MIT licence (LICENSE); these terms
   govern the hosted service and the official APK distribution described below, not your rights in the source under the
   MIT licence.
9. **Suspension and termination.** We or the Institution may suspend accounts that breach these terms or are rejected;
   you may stop using the service at any time and request deletion per the retention document.
10. **Disclaimers.** To the maximum extent permitted by law the service is provided "as is" without warranties of
    accuracy, fitness or uninterrupted operation. LectureX is a coordination tool. It does not replace the Institution's
    timetable, its attendance rules or its own substitution arrangements.
11. **Liability.** To the maximum extent permitted by law we are not liable for indirect or consequential loss, including
    missed, cancelled or double-booked classes; substitutions not found, not accepted or not confirmed; notifications
    that arrive late or not at all; schedule errors from imports; and loss of data. Aggregate liability is limited to
    `[amount - counsel]`. Nothing excludes liability that cannot be excluded.
12. **Governing law and disputes.** `[GOVERNING_LAW]`; courts or arbitration at `[VENUE]`. Consumer rights that cannot be
    waived remain.
13. **Changes to terms.** We will update the effective date and, for material changes, notify you in-app (Planned).
14. **Contact.** `[CONTACT_EMAIL]`; India grievance officer `[GRIEVANCE_OFFICER]`.

## Distribution of the Android app

- **Official source only.** The Android app is distributed as an APK file from the official GitHub Release on the public
  repository `Zenithquonta/lecturex-releases`, or from a link your administrator gives you. Download only from those
  links. Do not use APK files from other websites, forums, chat groups or file-sharing services.
- **Check the checksum.** Each release publishes a SHA-256 checksum for its APK. Before installing, compare the checksum
  of the file you downloaded with the value published for that release. Do not install the file if they do not match.
  Commands: `sha256sum` (Linux, macOS, Git Bash) or `Get-FileHash -Algorithm SHA256` (Windows PowerShell).
- **Debug-signed builds.** Current LectureX builds are signed with a debug key. They are not published through, reviewed by
  or signed for Google Play. Android may warn that the app comes from an unknown source. Allowing installs from unknown
  sources is your decision and your responsibility; turn that permission off again after installing if you do not need it.
- **Provided as is.** Section 10 applies to the APK. We do not warrant that an APK is free of defects, and the
  distribution method is a pre-release arrangement that may change.
- **Redistribution.** You may share the official APK only unchanged, with its official link and its published checksum.
  An APK that is modified, re-signed, rebuilt or repackaged is not an official LectureX release. We do not support it and
  are not liable for it. Building the app yourself from the MIT-licensed source under section 8 is permitted, but a build
  you make is not an official release and must not be presented as one.
- **Other sources.** We are not liable for any harm caused by an APK obtained from a source other than the official link,
  or by a modified or redistributed build.

## Updates

- **Updates are manual.** The app can tell you that a newer version is published ("Check for Updates"), but it does not
  download or install anything itself. You install an update by downloading the new APK from the official link and
  installing it over the existing app. An update keeps your data only when it is signed with the same key.
- **Latest version only.** Only the latest published version is supported. Older versions may stop working when backend
  changes are deployed, without an additional notice to you beyond the release note.
- **No guarantee of hosting.** We do not guarantee that the GitHub hosting of the APK, or the update-check service, will
  remain available. If the official link is unavailable, use the version you already have, or contact your administrator.

## Substitution offers

- **What an offer is.** A requester may invite one or more eligible faculty to cover one lecture. The invitations are
  ranked in a priority order. The requester chooses one faculty member who has accepted. That choice then goes to the
  division coordinator for approval. The lecture timetable changes only after coordinator approval.
- **Coordination only.** The app does not guarantee that a substitute will be found, that anyone will accept, that a
  faculty member will be available at the time, or that notifications will arrive on time. Notifications appear inside
  the app, so do not rely on the app alone for an urgent arrangement. Requesters and faculty should also tell the
  coordinator or administrator directly when a lecture is at risk.
- **Institutional confirmation.** The final arrangement is subject to coordinator and Institution approval. Faculty remain
  responsible for confirming cover with the Institution, and for following the Institution's rules on absence, cover and
  attendance.
- **Accepting is a commitment.** An acceptance tells the requester you are available to cover the lecture. The app does
  not let you change your response once it is given. If you can no longer cover after accepting, tell the requester and
  the coordinator immediately so they can make another arrangement.
- **Confidentiality.** An offer shows the lecture, its time, the requester and the other faculty invited to the same lecture
  (see [Privacy Policy](PRIVACY_POLICY.md), section on substitution offers). Invited faculty and the other people listed
  there may see these details. Do not copy, screenshot or share offer details outside the Institution or with people who
  do not need them for the arrangement.
- **Misuse.** Spamming offers, accepting without an intention to cover, and similar conduct are prohibited by the
  [Acceptable Use Policy](ACCEPTABLE_USE_POLICY.md).

## Service and publication commitments

- **Fees and refunds.** The current pre-release app has no paid plan, checkout or in-app purchase, so no app fee or refund
  is currently charged or offered. If paid services are introduced, display the full price and any recurring charges
  before purchase, publish the applicable cancellation and refund terms, and avoid hidden fees or misleading prompts.
- **Accurate claims and reviews.** Product descriptions should identify features that are implemented and tested. Do not
  publish fabricated testimonials, fake reviews or unsupported performance or compliance claims. The repository's
  evidence and implementation status describe current limits.
- **Accessibility.** Provide meaningful text alternatives for informative images and icons, sufficient text contrast and
  keyboard or assistive-technology access to interactive controls. These are release goals, not a claim that the current
  app passes an accessibility audit; see the [accessibility statement](ACCESSIBILITY_STATEMENT.md).
- **Content rights.** Use fonts, images and other third-party assets only with the rights needed for distribution, and
  preserve required attribution. The [third-party licence inventory](THIRD_PARTY_LICENSES.md) still needs verification
  before release.
- **Operator details.** Before publishing, replace the operator, address, institution, contact, grievance and dispute
  placeholders in these terms and the [Privacy Policy](PRIVACY_POLICY.md) with the actual business details.

## Changes in this version (2026-10-14)

- Added the student-project and non-commercial statement, and the precedence of Institution policy and the official
  timetable.
- Section 2 and section 7: substitution offers, backend availability and download-host availability.
- Section 8: clarified that the MIT licence governs the source, and that these terms govern the hosted service and the
  official APK distribution.
- Section 10 and section 11: coordination-only nature of the app, and the scheduling, substitution, notification and
  data-loss matters for which liability is excluded to the extent the law allows.
- New sections: Distribution of the Android app, Updates, Substitution offers.
- Counsel review is still required. Placeholders in brackets are unchanged.
