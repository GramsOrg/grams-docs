
## Node JS

This section will walk you through some basic examples of how to use the Grams SDK with Node.js.

### Prerequisites

Before starting, you will need to have the following:

-   Node.js installed on your machine
-   An active account on the TON blockchain with some Grams in it
-   The Grams SDK installed and initialized in your project

### Step 1: Import the SDK

To use the Grams SDK in your Node.js project, you will first need to import it into your script:

```
const { Wallet } = require('grams-sdk');
```

### Step 2: Initialize the SDK

Next, you will need to initialize the SDK with your credentials:

```
const wallet = new Wallet({
	network: 'mainnet',
	apiKey: 'YOUR_API_KEY',
	apiSecret: 'YOUR_API_SECRET'
});
```

In the `network` parameter, you can choose between `mainnet` or `testnet`, depending on which network you want to use. In the `apiKey` and `apiSecret` parameters, you will need to input your personal API key and secret, which you can obtain by registering on the Grams website.

### Step 3: Connect to Your Account

Once you have initialized the SDK, you can connect to your TON blockchain account by using the `login` method:

```
await wallet.login('YOUR_USERNAME', 'YOUR_PASSWORD');
```

Replace `YOUR_USERNAME` and `YOUR_PASSWORD` with your actual account credentials.

### Step 4: Check Your Account Balance

You can check your account balance by using the `getBalance` method:

```
const balance = await account.getBalance();
console.log(`Your account balance is ${balance} Grams.`);
```

### Step 5: Send Grams to Another Account

To send Grams to another account, you can use the `sendTransaction` method:

```
const recipient = 'RECIPIENT_ADDRESS';
const amount = 100; // In nanograms (1 Gram = 1,000,000,000 nanograms)
const transaction = await account.sendTransaction(recipient, { amount });
console.log(`Transaction ID: ${transaction.id}`);
```

Replace `RECIPIENT_ADDRESS` with the address of the account you want to send Grams to.

### Step 6: Monitor Transactions

You can monitor incoming and outgoing transactions to your account by using the `listen` method:

```
account.listen({ type: 'transaction' }, (event) => {
	console.log(`New transaction: ${event.id}`);
});
```

This will create a listener that will print the ID of any new incoming or outgoing transaction to your account.

### Step 7: Disconnect from Your Account

Finally, once you are done using the Grams SDK, you can disconnect from your TON blockchain account by using the `logout` method:

```
await account.logout();
```

This will close the connection to your account and ensure that no one can access it without your permission.

That's it for this basic example walkthrough! From here, you can explore more of the Grams SDK documentation to learn about the many other features and capabilities of the SDK.