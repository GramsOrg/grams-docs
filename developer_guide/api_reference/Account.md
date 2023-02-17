## `Account`

Represents a single account within the wallet.

----

### `generateAddress()`

Generates a new address for this account.

#### Parameters

-   None

#### Returns

-   `address` (string): The new address generated.

#### Errors

-   `AddressGenerationError`: Raised if a new address could not be generated.

#### Example

```
const address = account.generateAddress();
console.log(`New address: ${address}`);
````

----

### `getBalance(options)`

Gets the balance of this account.

#### Parameters

-   `options` (object, optional):
    -   `confirmations` (number, optional): The number of confirmations required for a transaction to be considered as settled. Default value is 0.

#### Returns

-   `balance` (object):
    -   `total` (number): The total balance in the smallest unit of the currency (e.g. cents for USD).
    -   `available` (number): The balance that is available for spending, in the smallest unit of the currency.

#### Errors

-   `BalanceError`: Raised if the balance could not be retrieved.

#### Example

```
const balance = account.getBalance();
console.log(`Total balance: ${balance.total}`);
console.log(`Available balance: ${balance.available}`);
````

----

### `getAddress()`

Gets the current address for this account.

#### Parameters

-   None

#### Returns

-   `address` (string): The current address for this account.

#### Example

```
const address = account.getAddress();
console.log(`Current address: ${address}`);
```

----

### `getTransactions(options)`

Gets a list of all transactions associated with this account.

#### Parameters

-   `options` (object, optional):
    -   `limit` (number, optional): The maximum number of transactions to return. Default value is 10.
    -   `offset` (number, optional): The number of transactions to skip before returning results. Default value is 0.
    -   `type` (string, optional): The type of transactions to filter by (e.g. 'sent', 'received', 'all'). Default value is 'all'.
    -   `start` (number, optional): The start time of the transactions to filter by (in Unix time). Default value is 0.
    -   `end` (number, optional): The end time of the transactions to filter by (in Unix time). Default value is the current time.

#### Returns

-   `transactions` (array): An array of transaction objects, each with the following properties:
    -   `id` (string): The ID of the transaction.
    -   `amount` (number): The amount of the transaction in the smallest unit of the currency.
    -   `type` (string): The type of transaction (e.g. 'sent', 'received').
    -   `timestamp` (number): The timestamp of the transaction in Unix time.
    -   `from` (string): The address the transaction was sent from.
    -   `to` (string): The address the transaction was sent to.
    -   `status` (string): The status of the transaction (e.g. 'pending', 'settled').

#### Errors

-   `TransactionError`: Raised if the list of transactions could not be retrieved.

#### Example

```
const transactions = account.getTransactions();
console.log(`Number of transactions: ${transactions.length}`);
console.log(`First transaction: ${JSON.stringify(transactions[0])}`);
```

----

### `getTransaction(id)`

Returns transaction data based on the transaction id.

#### Parameters

-   `id` (string): Transaction id.

#### Returns

-   `transaction` (object): Transaction object with the following properties:
    -   `id` (string): Transaction id.
    -   `hash` (string): Transaction hash.
    -   `from` (string): Sender address.
    -   `to` (string): Receiver address.
    -   `value` (number): Amount transferred.
    -   `gas` (number): Gas limit.
    -   `gasPrice` (number): Gas price.
    -   `nonce` (number): Nonce.
    -   `timestamp` (number): Timestamp of the transaction.

#### Errors

-   `InvalidTransaction`: Raised if the transaction is invalid or does not exist.

#### Example

```
const transaction = account.getTransaction('0x123456789abcdef');
console.log(transaction);
```

---

### `sendTransaction(receipient, options)`

Sends a transaction from the account to the specified recipient.

#### Parameters

-   `recipient` (string): Recipient address.
-   `options` (object): Object with the following properties:
    -   `value` (number): Amount to be transferred.
    -   `gas` (number): Gas limit.
    -   `gasPrice` (number): Gas price.
    -   `nonce` (number): Nonce.
    -   `data` (string): Data to include in the transaction.

#### Returns

-   `transaction` (object): Transaction object with the following properties:
    -   `id` (string): Transaction id.
    -   `hash` (string): Transaction hash.
    -   `from` (string): Sender address.
    -   `to` (string): Receiver address.
    -   `value` (number): Amount transferred.
    -   `gas` (number): Gas limit.
    -   `gasPrice` (number): Gas price.
    -   `nonce` (number): Nonce.
    -   `timestamp` (number): Timestamp of the transaction.

#### Errors

-   `InvalidTransaction`: Raised if the transaction is invalid or could not be sent.

#### Example

```
const transaction = account.sendTransaction('0x123456789abcdef', {
	value: 1000000000000000, // 0.001 GRM
	gas: 21000,
	gasPrice: 1000000000, // 1 Gwei
	nonce: 1,
}); 
console.log(transaction);
```

---

### `sendAmount(recipient, amount, options)`

Sends a specified amount of grams to the given recipient address or a specified amount of tokens to the recipient's address, from the current account.

#### Parameters

-   `recipient` (string): The address of the recipient.
-   `amount` (number): The amount to send, in nanograms (10^(-9) grams) for grams or in tokens for tokens.
-   `options` (object, optional): Additional options for the transaction. Possible options are:
    -   `message` (string): An optional message to include with the transaction.
    -   `token` (string, optional): The symbol of the token to send. Only required if sending tokens.
    -   `decimals` (number, optional): The number of decimal places for the token. Only required if sending tokens.

#### Returns

-   `txId` (string): The ID of the transaction.

#### Errors

-   `InsufficientFunds`: Raised if the account has insufficient balance to complete the transaction.
-   `InvalidAddress`: Raised if the recipient address is invalid.
-   `InvalidToken`: Raised if the token is invalid or not supported.
-   `InvalidDecimals`: Raised if the number of decimals is invalid or not supported.
-   `TransactionFailed`: Raised if the transaction failed for any other reason.

#### Example

```
// Send 1 gram to recipient address
const txId = account.sendAmount("recipient_address", 1e9);

// Send 10 tokens to recipient address 
const txId = account.sendAmount("recipient_address", 10, {
	token: "FOO", decimals: 18 
});
```

----

### `mintToken(options)`

Mints a new token on the blockchain and returns the token ID.

#### Parameters

-   `options` (object):
    -   `name` (string): Name of the token to be minted.
    -   `symbol` (string): Symbol of the token to be minted.
    -   `decimals` (number): Number of decimal places for the token.
    -   `totalSupply` (number): Total supply of the token.

#### Returns

-   `tokenId` (string): ID of the minted token.

#### Errors

-   `InvalidToken`: Raised if the token is invalid or could not be minted.

#### Example

```
const tokenId = await account.mintToken({
	name: 'My Token',
	symbol: 'MTK',
	decimals: 18,
	totalSupply: 1000000
}); 
console.log(tokenId); // Output: 0x123456789abcdef
```

----

### `getTokens()`

Returns a list of all tokens owned by the account.

#### Parameters

-   None.

#### Returns

-   `tokens` (array): An array of objects representing each token.
    -   `id` (string): ID of the token.
    -   `name` (string): Name of the token.
    -   `symbol` (string): Symbol of the token.
    -   `decimals` (number): Number of decimal places for the token.
    -   `totalSupply` (number): Total supply of the token.
    -   `balance` (number): Account balance of the token.

#### Example

```
const tokens = await account.getTokens(); 
console.log(tokens); 
// Output: [{ id: '0x123456789abcdef', name: 'My Token', symbol: 'MTK', decimals: 18, totalSupply: 1000000, balance: 100 }]
```

----

### `listen(options, callback)`

Starts listening for incoming transactions and invokes the callback function when a new transaction is received.

#### Parameters

-   `options` (object):
    -   `confirmations` (number): Number of confirmations required for the transaction to be considered confirmed.
-   `callback` (function): Function to be invoked when a new transaction is received. The function should take one argument representing the transaction.

#### Returns

-   `listener` (object): A listener object that can be used to stop listening.

#### Example

```
const listener = account.listen({ confirmations: 3 }, (transaction) => {
	console.log('New transaction received: ', transaction);
});
```

----

### `stopListening(options)`

Stops listening for incoming transactions.

#### Parameters

-   `options` (object):
    -   `listener` (object): The listener object to be stopped.

#### Returns

-   None.

#### Example

```
account.stopListening(listener);
```
