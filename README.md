# Tic Tac Toe App

## Overview

This Tic Tac Toe app allows users to play the classic game either offline or online. It integrates with Firebase Realtime Database for real-time chat functionality and Cloud Firestore for game state management. Users can join or create games online and communicate through a chat interface.

## Features

- **Play Offline:** Users can play Tic Tac Toe against a friend on the same device.
- **Create/Join Online Game:** Users can create or join a game online using a unique game ID.
- **Real-time Chat:** Integrated Firebase Realtime Database for real-time chat between players.
- **Game State Management:** Uses Firebase Cloud Firestore to store and manage game state.

## Getting Started

### Prerequisites

- [Android Studio](https://developer.android.com/studio) with the latest SDK.
- [Firebase Account](https://firebase.google.com/) and Firebase project setup.
- [Google Services JSON](https://firebase.google.com/docs/android/setup) file added to your project.

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Milind-Ranjan/TicTacToe.git
2. Open the project in Android Studio:
	- Launch Android Studio.
	- Select Open and navigate to the project directory.
3. Add Firebase to your project:
   	- Follow the Firebase setup instructions to add Firebase to your Android project.
	- Download the google-services.json file and place it in the app/ directory.
4. Add Firebase dependencies:
   In your build.gradle files (both project and app-level), add the necessary Firebase dependencies:
	```bash
	// Project-level build.gradle
	buildscript {
    	dependencies {
        	classpath 'com.google.gms:google-services:4.3.15' // Update to latest version
    	}
	}

	// App-level build.gradle
	dependencies {
    	implementation 'com.google.firebase:firebase-auth:22.0.0' // Update to latest version
    	implementation 'com.google.firebase:firebase-database:20.0.0' // Update to latest version
    	implementation 'com.google.firebase:firebase-firestore:24.0.0' // Update to latest version
	}

	apply plugin: 'com.google.gms.google-services'
 6. Configure Firebase Realtime Database:
	- Go to the Firebase Console and navigate to Realtime Database.
	- Set the database rules to allow authenticated users only (as defined earlier).
7. Run the app:
	- Connect an Android device or start an emulator.
	- Click on the Run button in Android Studio.


## File Structure

- app/src/main/java/com/yourapp/: Contains Java/Kotlin source files.
- app/src/main/res/layout/: Contains XML layout files.
- app/src/main/res/values/colors.xml: Defines color resources.
- app/src/main/res/values/strings.xml: Defines string resources.
- app/src/main/res/values/styles.xml: Defines style resources.
- app/src/main/res/xml/: Contains Firebase configuration files.

Cloud Firestore Structure

- games: Collection storing game data with documents for each game.
- chats: Subcollection under each game document for chat messages.

Contributing

1.	Fork the repository.
2.	Create a new branch (git checkout -b feature-branch).
3.	Commit your changes (git commit -am 'Add new feature').
4.	Push to the branch (git push origin feature-branch).
5.	Create a new Pull Request.

## Firebase Setup

Realtime Database Rules
```bash
{
  "rules": {
    "tictactoe": {
      "games": {
        "$gameId": {
          "chats": {
            ".read": "true",
            ".write": "true"
          }
        }
      }
    }
  }
}

