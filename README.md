# Lost & Found App

![Platform](https://img.shields.io/badge/platform-Flutter-02569B?logo=flutter&logoColor=white)
![Language](https://img.shields.io/badge/language-Dart-0175C2?logo=dart&logoColor=white)
![Backend](https://img.shields.io/badge/backend-Firebase-FFCA28?logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/license-MIT-green)

A Flutter app that helps a campus or organization manage lost and found items. Users can browse reported items with photos and locations, while admins manage the item catalog and log items as returned/claimed with the claimant's details.

## Demo

▶️ [Watch the demo](https://youtu.be/SpnijFD44js)

## Features

**For users:**
- Browse all reported lost & found items with photo, name, description, location, and report date
- Live-updating item list backed by Cloud Firestore

**For admins (authenticated):**
- Secure admin login with Firebase Authentication
- Add new found items with photo upload, name, description, and location
- Edit or delete existing item listings
- Move an item to **History** once claimed, recording the claimant's full name, national ID, student ID, and claim date
- Browse claim history with full claimant details

**Under the hood:**
- Image upload and hosting via Firebase Storage
- Real-time data via Cloud Firestore collections (`lostandfound`, `lostandfoundhistory`)
- Firebase Analytics integration

## Tech Stack

| | |
|---|---|
| **Framework** | Flutter |
| **Language** | Dart |
| **Auth** | `firebase_auth` (admin login) |
| **Database** | `cloud_firestore` |
| **File Storage** | `firebase_storage` (item images) |
| **Analytics** | `firebase_analytics` |
| **Image Picking** | `image_picker` |
| **Other** | `intl` (date formatting), `hexcolor`, `flutter_cache_manager` |

## Project Structure

```
Lost-And-Found-App/
├── lib/
│   ├── main.dart                          # App entry point
│   ├── firebase_options.dart              # Firebase configuration
│   ├── adminAuth/
│   │   └── admin_auth.dart                # Admin login/logout via Firebase Auth
│   ├── backend_service/
│   │   ├── backend_service.dart           # Firestore/Storage CRUD: upload, update, delete, history
│   │   ├── backend_exceptions.dart        # Custom exception types
│   │   └── inti.dart                      # Firebase initialization helper
│   ├── componet/                          # Reusable widgets (buttons, text fields, list builders)
│   └── screens/
│       ├── userScreen/                    # Home, item browsing, item details
│       └── adminScreens/
│           ├── mainAdminScreens/          # Admin login, dashboard, item list, history
│           └── mainAdminOperations/       # Add/update item, move item to history, history details
├── images/                                 # App image assets
└── pubspec.yaml
```

## Getting Started

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install)
- Android Studio / VS Code with the Flutter extension
- A [Firebase project](https://console.firebase.google.com/) with Authentication, Firestore, and Storage enabled

### Setup

```bash
git clone https://github.com/MoAbdullahConQ/Lost-And-Found-App.git
cd Lost-And-Found-App
flutter pub get
```

Connect your own Firebase project by running the [FlutterFire CLI](https://firebase.google.com/docs/flutter/setup) to regenerate `firebase_options.dart`:

```bash
flutterfire configure
```

Run the app:

```bash
flutter run
```

## How It Works

Users land on a home screen that streams all documents from the `lostandfound` Firestore collection, showing each item's photo, name, description, and location in real time. Admins authenticate via Firebase Auth to access a dashboard where they can add items (uploading a photo to Firebase Storage and writing the metadata to Firestore), edit or delete listings, and — once an item is claimed — move it to the `lostandfoundhistory` collection along with the claimant's identifying details for record-keeping.

## Author

**Muhammed Abdullah**
- GitHub: [@MoAbdullahConQ](https://github.com/MoAbdullahConQ)
- LinkedIn: [muhammed-bn-abdullah](https://linkedin.com/in/muhammed-bn-abdullah)
- Email: muhammed.abdullah.01155849512@gmail.com

## License

This project is licensed under the [MIT License](LICENSE).
