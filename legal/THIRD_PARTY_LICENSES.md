# Third-party licences

> **TEMPLATE / inventory requiring verification by qualified counsel.** Versions are from `gradle/libs.versions.toml`.
> Licence names are the publishers' commonly stated licences from general knowledge and were **not** machine-verified
> against each artifact's POM; items marked *verify* must be checked. Regenerate with a licence-report Gradle plugin
> before release (Planned) and ship an in-app "Open source licences" screen (Planned; not present today).

| Library | Version | Use | Licence |
|---|---|---|---|
| AndroidX Core KTX | 1.19.0 | Android utilities | Apache-2.0 |
| AndroidX Lifecycle runtime / ViewModel Compose | 2.11.0 | Lifecycle | Apache-2.0 |
| AndroidX Activity Compose | 1.13.0 | Activity integration, document picker | Apache-2.0 |
| AndroidX Navigation Compose | 2.9.6 | Navigation | Apache-2.0 |
| AndroidX Security Crypto | 1.1.0 | Declared; no usage found in source | Apache-2.0 |
| Jetpack Compose BOM (UI, Graphics, Material3, Icons Core, Tooling) | 2026.02.01 | UI | Apache-2.0 |
| Kotlin / kotlinx-serialization-json | 2.4.10 / 1.9.0 | Language, JSON | Apache-2.0 |
| kotlinx-datetime | 0.7.1 | Date and time | Apache-2.0 |
| supabase-kt (BOM, postgrest-kt, auth-kt, functions-kt) | 3.8.0 | Backend client | MIT (*verify*) |
| Ktor client OkHttp | 3.5.2 | HTTP engine | Apache-2.0 |
| OkHttp (transitive) | per Ktor | HTTP | Apache-2.0 |
| Clerk Android API | 1.1.4 | Authentication | *verify* (see Clerk's repository and terms) |
| ML Kit Text Recognition | 16.0.1 | On-device OCR | Google ML Kit / Google APIs terms of service, not an open-source licence (*verify*) |
| JUnit | 4.13.2 | Unit tests (test only) | EPL-1.0 |
| AndroidX Test JUnit / Espresso / Compose UI test | 1.3.0 / 3.7.0 / BOM | Instrumented tests (test only) | Apache-2.0 |
| Supabase Edge runtime (Deno) | hosted | Edge Function | Hosted service; Deno is MIT |

The project itself is MIT licensed (LICENSE). Apache-2.0 requires reproducing the licence text and
NOTICE files in distributions; this is not yet done in the APK.
