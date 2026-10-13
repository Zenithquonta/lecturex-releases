# Data Processing and Subprocessors

> **TEMPLATE requiring review by qualified counsel.** Not legal advice. No data-processing agreement (DPA) is recorded in
> this repository; obtain and file the providers' current DPAs before handling real student data. Last updated: 2026-10-14.

## Roles

`[INSTITUTION_NAME]` (or the operator, if self-hosted) is the controller / data fiduciary; `[OPERATOR_LEGAL_NAME]` acts as
processor for the Institution where applicable; Clerk and Supabase are (sub)processors.

## Processors (hosted services)

| Processor | Data received | Purpose | Location | Contract |
|---|---|---|---|---|
| Clerk | Email, name, password (hashed), sessions, IP/device metadata inherent to authentication `[confirm in Clerk DPA]` | Authentication, email verification, JWKS | `[confirm]` | `[Clerk DPA - to file]` |
| Supabase | All application data except passwords, including substitution offers (`substitution_offers`) and published release metadata (`app_releases`); Edge Function runtime and secrets | Postgres, PostgREST, Edge Functions | `[SUPABASE_REGION]` | `[Supabase DPA - to file]` |
| GitHub (release host: public repository `Zenithquonta/lecturex-releases`) | No account or app data from the app. Receives the browser request, including IP address and browser user agent, when a user chooses to download an APK from its Releases page. Also hosts the release file itself | Hosting the signed APK for manual install | `[GitHub region - confirm]` | `[GitHub Terms / DPA - confirm applicability; no personal data is sent by the app]` |

The app's update check reads only the `app_releases` table in Supabase. It does not contact GitHub or any other host.
The APK download happens in the user's browser, not inside the app.

## SDKs bundled in the app (from `gradle/libs.versions.toml`, `app/build.gradle.kts`)

| SDK | Network behaviour | Personal data |
|---|---|---|
| Clerk Android 1.1.4 | Talks to Clerk | Yes (authentication) |
| supabase-kt 3.8.0 (Postgrest, Auth artifact, Functions) + Ktor/OkHttp | Talks to the configured Supabase URL. The Auth plugin is not installed in the client (Clerk token is supplied instead) | Yes (app data) |
| ML Kit Text Recognition 16.0.1 (bundled model) | On-device OCR. The bundled variant does not require model download; Google may collect SDK diagnostics `[confirm against ML Kit terms]` | Document content processed locally |
| AndroidX / Compose / kotlinx | Local libraries | No |
| `androidx.security:security-crypto` | Declared as a dependency; no use found in `app/src/main` | No |

No analytics, advertising, attribution or crash-reporting SDK was found.

## Transfer and safeguards checklist

- [ ] Execute DPAs; record sub-processor lists and change-notification routes.
- [ ] Record Supabase region and Clerk data location; assess cross-border transfer basis (GDPR Ch. V; DPDP s.16).
- [ ] Confirm breach-notification timelines from each provider.
- [ ] Confirm deletion/return of data on termination and backup retention.
- [ ] Restrict dashboard access to named administrators with MFA (provider consoles; app has no MFA - see Known
      limitations in docs/SECURITY.md).
- [ ] Keep `CLERK_SECRET_KEY` and `SUPABASE_SERVICE_ROLE_KEY` only in Edge secrets.
