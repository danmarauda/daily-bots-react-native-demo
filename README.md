# Daily Bots React Native Demo

A React Native demo application using Daily.co's SDK for video calls.

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js v18.18 (use the version specified in `.nvmrc`)
- npm or yarn
- For local builds:
  - [Xcode](https://developer.apple.com/xcode/) (iOS builds)
  - [Android Studio](https://developer.android.com/studio) (Android builds)

## API Key Setup

1. Create a Daily.co account at https://dashboard.daily.co/signup
2. Get your API key from https://dashboard.daily.co/developers
3. Create a `.env` file in the project root (or edit if it exists):
```bash
EXPO_PUBLIC_BASE_URL=https://api.daily.co/v1/bots
EXPO_PUBLIC_DAILY_API_KEY=YOUR_DAILY_API_KEY_HERE
```
4. Replace `YOUR_DAILY_API_KEY_HERE` with your actual Daily.co API key

## Important Note About Expo

⚠️ This project **cannot** be used with [Expo Go](https://docs.expo.dev/workflow/expo-go/) because it requires custom native code. Instead, you'll need to use a [development build](https://docs.expo.dev/development/introduction/).

The custom native code used by this demo is provided by [rn-daily-js-expo-config-plugin](https://github.com/daily-co/rn-daily-js-expo-config-plugin).

## Installation & Setup

1. Install the correct Node.js version:
```bash
nvm i
```

2. Install dependencies:
```bash
npm i
```

3. Generate native source code:
```bash
npx expo prebuild
```

## Running the App

You have two options for building and running the app:

### Option 1: Building Remotely (Recommended for beginners)

If you don't have experience with Xcode and Android Studio or don't have them installed locally:

1. Follow [Expo's guide to use EAS Build](https://docs.expo.dev/development/create-development-builds/#create-and-install-eas-build)

### Option 2: Building Locally

#### For Android

1. Connect an Android device [configured for debugging](https://developer.android.com/studio/debug/dev-options)
2. Run:
```bash
npm run android
```

#### For iOS

##### First-time Setup

1. Open `ios/RNDailybots.xcworkspace` in Xcode
2. Add your Apple Developer account:
   - Open Xcode → Settings → Accounts
   - Click '+' to add an account (Apple ID)
   ![Xcode Accounts](./docsAssets/xcode-accounts.png)

3. Configure signing:
   - Close Settings
   - Select folder icon in top left
   - Select 'RNDailybots' from side panel
   - Navigate to 'Signing & Capabilities'
   - Open "Team" dropdown
   - Select your account
   ![Xcode Signing](./docsAssets/xcode-signing.png)

4. Run the app:
```bash
npm run ios
```

## Troubleshooting

### iOS Issues

1. **Invalid Bundle Identifier**
   - Error: "Change your bundle identifier to a unique string to try again"
   - Solution: Update the "Bundle Identifier" in Xcode's Signing & Capabilities to make it unique

2. **Invalid Code Signature**
   - Error: "Xcode was unable to launch because it has an invalid code signature..."
   - Solution:
     1. Open iPhone Settings
     2. Go to General → Device Management
     3. Trust DailyPlayground

3. **Keychain Access**
   - If prompted for login keychain password, select "Always trust" to prevent repeated prompts

### Daily.co API Issues

1. **Authentication Error**
   - Error: "Error occurred: [Error]"
   - Solution: Verify your Daily.co API key is correctly set in the `.env` file

2. **Connection Issues**
   - Make sure you have a stable internet connection
   - Verify the EXPO_PUBLIC_BASE_URL is set correctly in `.env`
   - Check if your Daily.co account is active and in good standing
