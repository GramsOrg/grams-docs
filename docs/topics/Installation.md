## Installing grams-sdk

The Grams SDK offers comprehensive support for building decentralized applications (dApps) on various platforms, including JavaScript, Android, and Unity. This guide outlines the steps to install and set up the Grams SDK for each platform.

## Node JS

### Prerequisites

* Node.js version 12.x or higher
* NPM package manager

### Steps

1. Open your terminal and navigate to your project directory.
2. Run the following command to install the Grams SDK as a dependency:

```
npm install @grams/sdk
```

3.  Import the SDK to your project:

```
const { Wallet, Passport } = require('@grams/sdk');
```

4.  Use the SDK by instantiating a new Grams SDK object:

```
const wallet = new Wallet();
```

## Android

### Prerequisites

* Android Studio 4.0 or higher

### Steps

1. Clone the Grams SDK repository to your local machine

```
git clone https://github.com/gramsio/grams-sdk-android.git
```

2.  Open the project in Android Studio.
3.  Build and run the project on your device or emulator.
4. Once you have installed the Grams SDK for Android, you can use it in your application by adding the following code to your project

```
import io.grams.sdk.Grams.Wallet;
import io.grams.sdk.Grams.Passport;

// Initialize the Grams SDK
Wallet wallet = new Wallet();
Passport wallet = new Passport();
```

## Unity

### Prerequisites

* Unity 2018 or higher

### Steps

1.  Open your Unity project.
2.  Import the Grams SDK package into your project.
3. Once you have installed the Grams SDK for Unity, you can use it in your project by adding the following code

```
using GramsSdk.Wallet;
using GramsSdk.Passport;

// Initialize the Grams SDK
var wallet = new Wallet();
var passport = new Passport();
```

Congratulations, you have successfully installed the Grams SDK on your preferred platform. You are now ready to start building dApps on the Grams network.