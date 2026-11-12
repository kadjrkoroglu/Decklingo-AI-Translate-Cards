<div align="center">

<img src="media/icon.png" width="112" alt="Decklingo icon">

# Decklingo: AI Translate-Cards

**Translate with AI, save the words you meet and learn them with spaced repetition.**

[![Download on the App Store](https://img.shields.io/badge/App_Store-Download-0D96F6?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/app/id6824556221)

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-DD2C00?style=flat-square&logo=firebase&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)

An iOS app I designed, built and shipped on my own:<br>
a Flutter client, a Node.js backend on Firebase, AI with Google Gemini and in-app subscriptions.

<br>

<a href="media/decklingo-promo.mp4"><img src="media/preview.gif" width="260" alt="Decklingo promo"></a>

<sub>▶ <a href="media/decklingo-promo.mp4">Watch the full promo video</a></sub>

</div>

<br>

## 📱 Screenshots

<table align="center">
  <tr>
    <td align="center"><img src="screenshots/01-translate.jpg" width="230"><br><b>Translate</b><br><sub>Standard, Formal or Slang</sub></td>
    <td align="center"><img src="screenshots/10-examples.jpg" width="230"><br><b>Examples</b><br><sub>Five sentences for any word</sub></td>
    <td align="center"><img src="screenshots/02-photo.jpg" width="230"><br><b>Photo</b><br><sub>Translate text from the camera</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/04-save.jpg" width="230"><br><b>Save</b><br><sub>Any translation to a deck</sub></td>
    <td align="center"><img src="screenshots/07-decks.jpg" width="230"><br><b>Decks</b><br><sub>See what's due at a glance</sub></td>
    <td align="center"><img src="screenshots/05-learn.jpg" width="230"><br><b>Learn</b><br><sub>Swipe to rate each card</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/09-study.jpg" width="230"><br><b>Study with AI</b><br><sub>Fill-in-the-blank practice</sub></td>
    <td align="center"><img src="screenshots/06-practice.jpg" width="230"><br><b>Practice</b><br><sub>Answers checked instantly</sub></td>
    <td align="center"><img src="screenshots/03-live.jpg" width="230"><br><b>Live</b><br><sub>Speech translated as it's spoken</sub></td>
  </tr>
</table>

## ✨ Features

| | |
|---|---|
| 🌐 **AI translation** | Standard, Formal or Slang tone, with up to three alternatives |
| 💬 **Example sentences** | Five everyday sentences, the word highlighted in both languages |
| 📷 **Photo translation** | Text is read on the device; only the text is sent, never the photo |
| 🎙️ **Live translation** | Speech translated as it is spoken, with captions (Gemini Live) |
| 🗂️ **Decks & flashcards** | Swipe-to-rate study with text-to-speech |
| 🧠 **Spaced repetition** | SM-2 based: missed cards return in the same session, reviews spread out by ease |
| ✍️ **Study with AI** | Fill-in-the-blank sentences written by the AI, answers checked on the server |
| ☁️ **Offline first** | Works without internet, syncs across devices when signed in |
| 🇬🇧 🇹🇷 **Two languages** | English and Turkish interface |

## 🏗️ Architecture

```
┌──────────────────────────────┐   HTTPS + Firebase ID token   ┌──────────────────────────────────┐
│ Flutter app (iOS)            │ ────────────────────────────► │ Express API on Cloud Functions   │
│                              │                               │                                  │
│ • Provider + MVVM            │                               │ • Firebase Auth on every route   │
│ • Isar local DB, offline     │                               │ • PostgreSQL (Supabase) + Prisma │
│ • Firestore sync per user    │                               │ • Per-plan quotas in SQL         │
│ • ML Kit text recognition    │                               │ • Gemini: translate, examples,   │
│ • RevenueCat subscriptions   │                               │   study, Live tokens             │
└──────────────────────────────┘                               │ • RevenueCat webhook → plans     │
                                                               └──────────────────────────────────┘
```

- 🔒 **Plans are enforced on the server.** The plan is read from RevenueCat, never trusted from the client; usage is counted atomically per plan window.
- 🔑 **API keys stay on the server.** The app gets short-lived tokens for live translation.
- 🛡️ **Privacy by design.** Per-user Firestore rules, no user text in logs, full account deletion.

## ✅ Quality

- 200+ unit and widget tests, run in CI with static analysis
- Security review and dependency audit before release

## 🔐 Source code

The source code is private. I'm happy to walk through it or share access on request.

<br>

<div align="center"><sub>© 2026 Kadir Köroğlu. All rights reserved.</sub></div>
