# Cookies and Tracking

> **TEMPLATE requiring review by qualified counsel.** Not legal advice.

**Finding: not applicable to the app as built.** LectureX is a native Android app. It has no web view, sets no browser
cookies, and contains no analytics, advertising, attribution or crash-reporting SDK and no advertising ID access (manifest
requests only `INTERNET`; dependency list reviewed). Therefore no cookie banner or ePrivacy/Consent-Mode mechanism is
needed for the app.

Qualifications to re-check before release:

- Clerk's hosted pages or web components, if ever used, may set cookies; the app currently uses the native Android SDK
  only. Re-assess if a web admin console is added.
- Network providers (Clerk, Supabase) log IP addresses in server logs as a normal part of operation; this is disclosed in
  the [Privacy Policy](PRIVACY_POLICY.md).
- The "Check for Updates" action opens the APK download link in the user's browser (Android `ACTION_VIEW`). The app sets
  no cookies for that step. The browser and the download host (GitHub Releases on `Zenithquonta/lecturex-releases`) handle any cookies or request
  logging under their own terms. Last updated: 2026-10-14.
- If analytics or crash reporting is added later, update this document, the Privacy Policy and
  [PLAY_DATA_SAFETY.md](PLAY_DATA_SAFETY.md), and obtain consent where required (GDPR/ePrivacy; DPDP).
