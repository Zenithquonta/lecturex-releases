# Accessibility statement

> **TEMPLATE requiring review.** This reports what the repository evidences; it is not a conformance claim. No WCAG,
> EN 301 549 or Section 508 audit has been performed, and the app is not certified.

## Measures in place (evidence)

- Material 3 components with large-text handling: larger-text labels and the four-role home screen were exercised at
  font scale 1.15 and about 360 dp width on a physical phone and emulator (`TEST_EVIDENCE.md`,
  `RoleUiDeviceVerificationTest`).
- Reduced-motion behaviour is implemented (`TEST_EVIDENCE.md` records animation scales set to zero during checks).
- Fixed light surface with navy/white tiers chosen for contrast (`DESIGN.md`); numeric contrast ratios were **not**
  measured or recorded.
- 15 `contentDescription` usages exist in `app/src/main`; coverage of every icon has not been audited.
- RTL support is declared (`android:supportsRtl="true"`); not tested.

## Known gaps

- No TalkBack walkthrough or Accessibility Scanner report is recorded.
- Touch target sizes and focus order are not audited; colour is used in calendar and status visuals and non-colour
  cues are not verified.
- English only; no localisation.
- No dark theme (the app deliberately forces a light surface).

## Plan

Run Accessibility Scanner and a TalkBack pass per role, record results in `TEST_EVIDENCE.md`, fix findings, then target
WCAG 2.2 AA. Feedback and accessibility requests: `[CONTACT_EMAIL]`.
