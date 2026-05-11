# Petden

Privacy-first pet health tracker for Android, iOS, and macOS.

This repository hosts Petden's **privacy policy** and **public issue tracker**.
It contains no source code - Petden is closed source. The privacy claims are
verifiable by inspecting the published APK / .app, not by reading the code
here.

## Privacy policy

Live at **[vivekyd6.github.io/petden-public](https://vivekyd6.github.io/petden-public/)**
(also available as [`index.md`](./index.md) in this repo).

## Issues

Bugs, feature requests, and questions: open an issue using one of the
templates. Security vulnerabilities and refund requests should go to
**vivekyadav36837@gmail.com** instead — please don't file those publicly.

## Verifying Petden's privacy claims

| Claim | How to verify |
| --- | --- |
| No `INTERNET` permission on Android | Extract the APK with [apktool](https://apktool.org), read `AndroidManifest.xml`. |
| No network entitlement on macOS Release | `codesign -d --entitlements - /Applications/Petden.app` |
| Zero outbound traffic at runtime | Install [PCAPdroid](https://emanuele-f.github.io/PCAPdroid/) (Android) or Little Snitch (macOS), run Petden for a day. |
| Empty App Store privacy nutrition labels | Open the Petden listing on the App Store - every category reads "Data Not Collected". |

## Contact

- General privacy questions: **vivekyadav36837@gmail.com**
- Public bug reports & feature requests: [Issues tab](../../issues)
