
## Node JS

Here's an example code walkthrough section for using the Grams SDK with Node.js:

```
const Grams = require('grams-sdk');

// Set up connection to Grams network
const grams = new Grams();

// Initialize wallet
const mnemonic = grams.wallet.init('myWallet', 'password');

// Log in to wallet
grams.wallet.login('myWallet', 'password');

// Create a new account
const account = grams.wallet.createAccount('myAccount');

// Generate a new address for the account
const address = account.generateAddress();

// Send tokens to another address
const recipient = '0x1234567890abcdef';
const amount = 100;
const options = {
  gas: 1000000,
  gasPrice: 20000000000
};
account.sendAmount(recipient, amount, options);

// Get account balance
const balance = account.getBalance();

// Get account transactions
const transactions = account.getTransactions();

// Get transaction by ID
const transactionId = '0x1234567890abcdef';
const transaction = account.getTransaction(transactionId);

// Mint new tokens
const tokenOptions = {
  name: 'MyToken',
  symbol: 'MTK',
  initialSupply: 1000000,
  decimals: 18,
  mintable: true
};
account.mintToken(tokenOptions);

// Get list of tokens
const tokens = account.getTokens();

// Listen for new transactions
const listener = account.listen({}, (transaction) => {
  console.log('New transaction:', transaction);
});

// Stop listening for new transactions
account.stopListening(listener);
```

This code demonstrates the basic usage of the Grams SDK with Node.js, including setting up a connection to the network, initializing a wallet, creating and managing accounts, sending transactions, and working with tokens.