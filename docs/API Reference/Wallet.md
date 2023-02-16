## `Wallet`

The Wallet module is used to manage Grams wallets. A wallet is a collection of accounts and is identified by a name.

### Constructor

```
const wallet = new Wallet(options)
```

Creates a new instance of the `Wallet` class.

#### Parameters

-   `options` (object, optional): Options to configure the `Wallet` instance.
    -   `endpoint` (string, optional): The URL of the Grams network endpoint. Default: `https://grams.network`.
    -   `network` (string, optional): The Grams network to connect to. Default: `mainnet`.

----

### `init(name, password, options)`

Initializes the wallet with a name and password and returns a mnemonic phrase.

#### Parameters

-   `name` (string): The name of the wallet.
-   `password` (string): The password to use to encrypt the wallet.
-   `options` (object, optional): Options to configure the `Wallet` instance.
    -   `mnemonic` (string, optional): The 24-word seed phrase to use to initialize the wallet.

#### Returns

-   `mnemonic` (string): Space separated 24-word seed string.

#### Errors

-   `InvalidWalletName`: Raised if the name is not a valid wallet name.
-   `InvalidWalletPassword`: Raised if the password is not a valid wallet password.
-   `WalletAlreadyExists`: Raised if a wallet with the given name already exists.

#### Example

```
const wallet = new Wallet()
const mnemonic = wallet.init('My Wallet', 'myPassword') 
console.log(mnemonic)
```

----

### `login(name, password)`

Logs into an existing wallet.

#### Parameters

-   `name` (string): The name of the wallet.
-   `password` (string): The password to use to decrypt the wallet.

#### Returns

-   None

#### Errors

-   `WalletNotFound`: Raised if a wallet with the given name does not exist.
-   `InvalidWalletPassword`: Raised if the password is incorrect.

#### Example

```
const wallet = new Wallet()
wallet.login('My Wallet', 'myPassword')
```

----

### `createAccount(name)`

Creates a new account in the wallet with the specified name.

#### Parameters

-   `name` (string): The name of the account.

#### Returns

-   An instance of the `Account` class representing the new account.

#### Errors

-   `InvalidAccountName`: Raised if the account name is invalid or already in use.

#### Example

```
const wallet = new Wallet()
wallet.login('My Wallet', 'myPassword')
const account = wallet.createAccount('My Account')
console.log(account.address)
```

----

### `getAccounts()`

Returns an array of all accounts in the wallet.

#### Parameters

-   None

#### Returns

-   An array of `Account` objects.

#### Errors

-   None

#### Example

```
const wallet = new Wallet()
wallet.login('My Wallet', 'myPassword')
const accounts = wallet.getAccounts() accounts.forEach(account => console.log(account.address))
```

----

### `getAccount(name)`

Returns the account with the specified name.

#### Parameters

-   `name` (string): The name of the account to return.

#### Returns

-   An instance of the `Account` class representing the account.

#### Errors

-   `AccountNotFound`: Raised if an account with the given name does not exist.

#### Example

```
const wallet = new Wallet()
wallet.login('My Wallet', 'myPassword')
const account = wallet.getAccount('My Account')
console.log(account.address)
```

----

### `changePassword(oldPassword, newPassword)`

Change the password of the currently logged in account.

#### Parameters

-   `oldPassword` (string): The current password for the account.
-   `newPassword` (string): The new password for the account.

#### Returns

-   None

#### Errors

-   `InvalidPassword`: Raised if the old password is incorrect or if the new password does not meet the password requirements.

#### Example

```
wallet.changePassword('oldpassword', 'newpassword')
```

----

### `backup(path, password)`

Backup the entire wallet to a file.

#### Parameters

-   `path` (string): The full path of the file to save the backup to.
-   `password` (string): The password to encrypt the backup file.

#### Returns

-   None

#### Errors

-   `InvalidBackupPath`: Raised if the backup path is not valid or if there is an issue saving the backup.
-   `InvalidPassword`: Raised if the password does not meet the password requirements.

#### Example

```
wallet.backup('/path/to/backup/file', 'backuppassword')
```

----

### `restore(path, password)`

Restore a wallet from a backup file.

#### Parameters

-   `path` (string): The full path of the backup file to restore from.
-   `password` (string): The password to decrypt the backup file.

#### Returns

-   None

#### Errors

-   `InvalidBackupPath`: Raised if the backup path is not valid or if there is an issue reading the backup.
-   `InvalidPassword`: Raised if the password does not meet the password requirements.

#### Example

```
wallet.restore('/path/to/backup/file', 'backuppassword')
```
