
## Installation

The Grams SDK offers comprehensive support for building decentralized applications (dApps) on various platforms, including JavaScript, Android, and Unity. This guide outlines the steps to install and set up the Grams SDK for each platform.

## Prerequisites

Before you get started, make sure you have the following:

-   A Grams developer account. If you don't have one, you can sign up [here](https://grams.com/developer).
-   Your Grams app ID and secret. You can get these from your Grams developer dashboard.

## Node JS

### Prerequisites

Before installing the SDK, ensure that the following prerequisites are installed:

-   Node.js version 14 or higher.
-   NPM package manager.

### Installation for Browser Applications

To install the SDK for use in browser applications, run the following command in your terminal:

```
npm install grams-sdk
```

### Installation for React Native Applications

To install the SDK for use in React Native applications, run the following command in your terminal:

```
npm install grams-sdk-react-native
```

### Installation for Desktop Applications

To install the SDK for use in desktop applications, run the following command in your terminal:

```
npm install grams-sdk-electron
```

### Initialization Example

After installing the SDK, you can initialize Grams by creating a new instance of the SDK and passing in the necessary configuration options:

```
const grams = require('grams-sdk');

// Set up your app credentials
const appId = 'YOUR_APP_ID';
const appSecret = 'YOUR_APP_SECRET';

// Initialize the Grams SDK
const sdk = new grams.SDK({
  appId,
  appSecret,
});

// Use the SDK to call an API method
sdk.getBalance((err, balance) => {
  if (err) {
    console.error('Error getting balance:', err);
  } else {
    console.log('Balance:', balance);
  }
});
```

By default, the SDK is initialized in test mode. To switch to production mode, pass the `mode: 'production'` option when initializing the SDK.

## Android

### Prerequisites

-   Android Studio 3.0 or later
-   Android API Level 21 or later
-   JDK 8 or later

### Installation

1.  Add the following to your app-level `build.gradle` file:

```
dependencies {
    implementation 'org.grams:grams-sdk:1.0.0'
}
```

2.  Sync your project with Gradle.

### Initialization

Here is an example of how to initialize the Grams SDK in an Android application:

```
import io.grams.sdk.Grams;
import io.grams.sdk.exceptions.InitializationException;

public class MainActivity extends AppCompatActivity {
    private static final String API_KEY = "your-api-key";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        try {
            Grams.initialize(getApplicationContext(), API_KEY);
        } catch (InitializationException e) {
            // handle initialization exception
        }
    }
}

```

## Swift

### Prerequisites

-   Xcode 11 or later
-   Swift 5.0 or later

### Installation

1.  Add the following to your `Podfile`:

```
target 'MyApp' do
  pod 'GramsSDK'
end
```

2.  Run `pod install`.

### Initialization

Here is an example of how to initialize the Grams SDK in a Swift application:

```
import GramsSDK

// Set up your app credentials
let appId = "YOUR_APP_ID"
let appSecret = "YOUR_APP_SECRET"

// Initialize the Grams SDK
let sdk = GramsSDK(appId: appId, appSecret: appSecret)

// Use the SDK to call an API method
sdk.getBalance { (balance, error) in
  if let error = error {
    print("Error getting balance:", error)
  } else {
    print("Balance:", balance)
  }
}
```

## Unity

### Prerequisites

-   Unity 2019.2 or later

### Installation

1.  Download the Grams Unity package from the [Grams SDK releases page](https://github.com/grams-io/grams-sdk/releases).
2.  Import the package into your Unity project.

### Initialization

Here is an example of how to initialize the Grams SDK in a Unity application:

```
using GramsSDK;

// Set up your app credentials
string appId = "YOUR_APP_ID";
string appSecret = "YOUR_APP_SECRET";

// Initialize the Grams SDK
var sdk = new SDK(appId, appSecret);

// Use the SDK to call an API method
sdk.GetBalance((balance, error) => {
  if (error != null) {
    Debug.LogError("Error getting balance: " + error);
  } else {
    Debug.Log("Balance: " + balance);
  }
});
```






### Prerequisites

* Node.js version 14.x or higher
* NPM package manager

### Steps

1. Open your terminal and navigate to your project directory.
2. Run the following command to install the Grams SDK as a dependency:

```
npm install grams-sdk
```

3.  Import the SDK to your project:

```
const { Wallet, Passport } = require('grams-sdk');
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

## Swift

### Prerequisites

* Swift 5.0 or higher.
* Xcode 11.0 or higher.
* iOS 11.0 or higher.
* Cocoapods 1.8.4 or higher.

### Steps

1.  Open Xcode and create a new project or open your existing project
2. Add the following to your `Podfile`

```
pod 'GramsSDK', '~> 1.0.0'
```

3. Run `pod install` to install the SDK
4. In your Swift file, import the Grams SDK module

```
import GramsSDK.Wallet

let wallet = Wallet.init()
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
