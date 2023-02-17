
## Creating a DApp with Grams SDK

In this walkthrough, we will create a simple DApp that uses the Grams SDK to connect to a Grams wallet and interact with an account.

### Prerequisites

Before starting, you will need the following installed on your machine:

-   Node.js (version 10 or higher)
-   npm or yarn package manager

### Installing the Grams Wallet Extension

To use the Grams Wallet extension, you will need to install it in your browser. You can find the extension on the Chrome Web Store or Firefox Add-ons marketplace.

### Project Setup

Once you have the extension installed, you can create a new React app by running the following command in your terminal:

```
npx create-react-app my-app
```

or if you are using yarn:

```
yarn create react-app my-app
```

This will create a new React app in the `my-app` directory.

Next, navigate into the directory and start the development server:

```
cd my-app npm start
```

or if you are using yarn:

```
cd my-app yarn start
```

You should now be able to view your React app in your browser at `http://localhost:3000`.

### Initializing and Connecting to the Grams Wallet Extension

To use the Grams Wallet extension in your React app, you need to initialize and connect to it.

First, add the following code to the `App.js` file in the `src` directory of your React app:

```
const grams = window.grams;
async function connect() {
	try {
		await grams.connect();
		console.log('Logged in successfully');
	} catch (error) {
		console.error(error);
	}
}
```

The `login` method will open a popup window with the Grams Wallet login screen, where you can enter your username and password.

### Connecting to an Account

After you have logged in, you can connect to your account using the `getAccount` method:

```
const grams = window.grams;
async function getAccount() {
	try {
		const account = await grams.getAccount();
		console.log('Connected to account', account);
	} catch (error) {
		console.error(error);
	}
}
```

This code will connect to the first account in the list of available accounts. If there are no accounts available, it will log a message

### Listening for changes on an account

To listen for changes on an account, you can use the `on` method provided by the `Account` class. This method allows you to register a listener function that will be called whenever there is a change to the account.

```
// Register a listener function to be called whenever there is a change to the account
account.on('change', () => {
	console.log(`Account ${account.name} has changed`);
});
```

In this example, we register a listener function that will be called whenever there is a change to the account. In this case, the listener function simply logs a message to the console.

### Sending a transaction

To send a transaction, you can use the `sendTransaction` method provided by the `Account` class. This method takes a recipient address and an amount as parameters, and returns a promise that resolves to the transaction ID when the transaction is confirmed.

```
// Send a transaction to a recipient
const recipient = '0x1234567890123456789012345678901234567890';
const amount = 1000;  
try {
	const txid = await account.sendTransaction(recipient, { amount });  
	console.log(`Transaction sent with ID: ${txid}`);
} catch (err) {
	console.error(`Error sending transaction: ${err.message}`);
}
```

In this example, we first send a transaction to a recipient using the `sendTransaction` method. The recipient is specified as a hexadecimal string, and the amount is specified in micrograms. The `sendTransaction` method returns a promise that resolves to the transaction ID when the transaction is confirmed. We wrap the call to `sendTransaction` in a try-catch block to handle any errors that may occur. If the transaction is successful, we log a message to the console with the transaction ID. If an error occurs, we log an error message to the console.

### Disconnect

Finally, we can disconnect from the Grams wallet using the `disconnect()` function:

```
wallet.disconnect()
.then(() => {
	console.log('Disconnected from Grams wallet'); })
.catch((err) => {
	console.error('Failed to disconnect from Grams wallet', err);
});
```

The `disconnect()` function returns a promise that resolves once the SDK has disconnected from the wallet.

### Conclusion

In this walkthrough, we created a simple DApp that uses the Grams SDK to connect to a Grams wallet and interact with an account. The Grams SDK provides a simple and powerful interface for interacting with the Grams blockchain, making it easy to create powerful and decentralized applications.