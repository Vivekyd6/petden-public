# Privacy Policy for Petden

**Last updated:** 11 May 2026
**Effective date:** 11 May 2026

Petden ("the app") is operated by Vivek Yadav. This policy describes
what information the app handles, why, and what choices you have. Petden
has been built so that **no personal data ever leaves your device**.

---

## 1. Summary

| Question                                            | Answer                                  |
| --------------------------------------------------- | --------------------------------------- |
| Does Petden collect personal data?                  | **No.**                                 |
| Does Petden send data over the internet?            | **No — the app has no network access.** |
| Does Petden use analytics or advertising?           | **No.**                                 |
| Does Petden share data with third parties?          | **No.**                                 |
| Does Petden require an account or login?            | **No.**                                 |
| Does Petden upload your pet's photos or records?    | **No — stored locally, encrypted.**     |

---

## 2. What the app does

Petden is a privacy-first pet health tracker. You record your pet's
vaccinations, medications, vet visits, weight, symptoms, and reminders
inside the app. Every record stays on the device you typed it into.

Pro features (PDF export, encrypted backup, advanced reminders, themes,
trend analytics) are unlocked through a one-time in-app purchase. The
purchase is processed by Google Play or the Apple App Store directly —
Petden never sees your payment details.

---

## 3. Information the app processes

All of the items below are stored on your device only. None are
transmitted to us or to any third party.

### 3.1 Pet records
The pets you register, their vaccinations, medications, vet visits,
weight history, symptom logs, and reminders. Stored in an encrypted
SQLite database in Petden's private app storage.

### 3.2 Photos
If you attach photos to a pet profile or a vet visit, the photo files
are stored locally and only their paths are recorded in the database.
The photos are never uploaded.

### 3.3 PIN / biometric metadata
If you choose to lock the app, Petden stores a PBKDF2-HMAC-SHA256 hash
of your PIN plus a randomly generated salt in the platform's secure
storage (Android Keystore / iOS Keychain). The PIN itself is never
stored. Biometric data is owned by the operating system; Petden only
receives a yes/no answer.

### 3.4 Database encryption key
A 256-bit key is generated on first launch and stored in the platform's
secure storage. Without it, the database cannot be decrypted. We never
receive a copy.

### 3.5 Pro entitlement cache
After a successful in-app purchase, Petden writes a small flag to
secure storage so the app does not have to re-query the store on every
launch. The flag contains no personal data.

### 3.6 App preferences
Theme choice, lock timeout, onboarding completion status, and similar
settings. Stored in the same secure storage and in the app's private
preferences file.

---

## 4. Permissions and why we need them

| Permission                          | Why it is requested                                       |
| ----------------------------------- | --------------------------------------------------------- |
| `POST_NOTIFICATIONS` (Android)      | Show local reminder notifications you scheduled.          |
| `SCHEDULE_EXACT_ALARM` (Android 12+) | Fire reminder notifications at the exact configured time. |
| `RECEIVE_BOOT_COMPLETED` (Android)  | Re-arm scheduled reminders after a phone restart.         |
| `USE_BIOMETRIC` / `USE_FINGERPRINT` | Authenticate the app lock with your device biometrics.    |
| Camera (iOS / macOS prompt)         | Used only if you take a photo from inside the app.        |
| Photo Library (iOS)                 | Used only if you attach a photo to a pet record.          |

Petden does **not** request the `INTERNET` permission on Android. You
can verify this by extracting the published APK with any free tool
(for example, [apktool](https://apktool.org)) and inspecting
`AndroidManifest.xml`. The line
`<uses-permission android:name="android.permission.INTERNET"/>` is
absent. Without that declaration, the operating system refuses to let
the app open network sockets.

On macOS, the Release build is sandboxed and is not granted
`com.apple.security.network.client`. You can verify this with:

```
codesign -d --entitlements - /Applications/Petden.app
```

---

## 5. Network usage

Petden does not make HTTP requests to our servers, to Google, to Apple,
or to any other host while running. The Android Release APK has no
INTERNET permission. The macOS Release `.app` has no network entitlement.
The iOS Release ships without any analytics, attribution, or telemetry
SDK that could initiate a network request.

The only network-adjacent operations the app supports are:

- **In-app purchase**: handled entirely by Google Play Billing or
  Apple StoreKit. Petden hands the purchase request to the operating
  system and reads back the success / failure result. We have no
  custom receipt-validation server.
- **Backup file selection** (Pro feature): when you tap "Export
  encrypted backup", Petden writes a passphrase-encrypted ZIP and uses
  the platform file picker (Storage Access Framework on Android, file
  picker on iOS / macOS) so you can save it wherever you like — your
  Drive, your Dropbox, your local Files. The destination is not chosen
  by Petden and the upload is performed by the OS-level integration
  with that destination, not by us.

---

## 6. Third parties

Petden contains **no analytics SDKs, no advertising SDKs, and no
crash-reporting SDKs**. We do not use Google Firebase, Google Analytics,
Meta SDKs, AppsFlyer, Adjust, RevenueCat, Sentry, or any similar
service.

The app does include the platform in-app purchase plugin
(`in_app_purchase`) so the Pro upgrade can be purchased through Google
Play or Apple's App Store. That plugin only talks to the platform store
when you tap "Unlock Pro" or "Restore purchases".

Open-source content bundled in the app:

- **Inter** font, licensed under the SIL Open Font License 1.1.
- **Geist** font, licensed under the SIL Open Font License 1.1.
- **Material Symbols** icons, licensed under Apache 2.0.

None of these involve a network call — the assets are bundled at build
time.

---

## 7. Children

Petden is not directed at children under 13. We do not knowingly collect
data from children, because we do not collect data from anyone.

---

## 8. Data retention and deletion

Because all data is stored only on your device:

- **You can delete it at any time.** Settings → Privacy & security →
  "Erase all data" wipes the entire encrypted database and the
  encryption key. The action is irreversible.
- **Uninstalling the app removes everything** — pet records, photos,
  reminders, lock setup, and the Pro entitlement cache.
- We have no remote copy of your data because we never receive it.

If you have purchased Pro and reinstall the app, "Restore purchases" on
the paywall will re-fetch your entitlement from Google Play or Apple's
App Store. Petden does not retain any record of who purchased what.

---

## 9. Security

The local database is encrypted at rest using SQLCipher (AES-256). The
encryption key is held only in your device's secure storage (Android
Keystore / iOS Keychain). The app sandbox prevents other apps on your
phone from reading the file.

Encrypted backups (Pro) use WinZip AES-256 with PBKDF2 key derivation
from your chosen passphrase. The passphrase is the only way to decrypt
the backup. If you forget it, the backup is unrecoverable — by design.

Because nothing is transmitted, there is no "in-transit" data to
encrypt.

---

## 10. Your rights

Since we hold no personal data about you, the GDPR / DPDP / CCPA right
to access, correct, port, or delete your data is satisfied by
controlling the data on your own device. Uninstalling Petden fulfils
the right to erasure in full.

If you have questions about this policy, see Section 13.

---

## 11. Children's data, sensitive data, financial data

Petden does not handle any of the following:

- Children's data (the app is not directed at children).
- Human medical data — Petden tracks pets only.
- Government or biometric IDs (biometric authentication uses the OS;
  we never see the template).
- Financial or payment data (handled entirely by Google Play / Apple
  StoreKit).
- SMS, call logs, contacts, location, or media beyond photos you
  explicitly attach to a pet record.

---

## 12. Changes to this policy

If this policy materially changes, the **Last updated** date above will
move forward and the change will be summarised in the app's release
notes on Google Play and the App Store. Continued use of the app after
a change means you accept the updated policy.

---

## 13. Contact

For privacy questions or concerns, email:

**petden.support@gmail.com**

We aim to respond within 7 working days. For bugs and feature requests,
please open an issue at
[github.com/vivekyd6/petden-public/issues](https://github.com/vivekyd6/petden-public/issues).
