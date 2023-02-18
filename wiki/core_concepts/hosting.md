
## Hosting

Grams hosting allows developers to serve their web applications on the decentralized web using the InterPlanetary File System (IPFS). By hosting your application on the decentralized web, you can benefit from its inherent security, privacy, and accessibility features. This means that your application will be more secure, available, and globally accessible.

### Getting Started

To get started with hosting your application on Grams, you will need to have a working knowledge of IPFS, and understand how it works. You will also need to have a Grams account to use as the host for your application.

### IPFS Hosting

Grams provides IPFS hosting for web applications, allowing developers to serve their applications on the decentralized web. To host your application on IPFS, you will need to create a JSON file that contains the necessary configuration settings.

#### Hosting JSON Configuration

The hosting configuration JSON file should include the following fields:

-   `name`: The name of the application.
-   `description`: A short description of the application.
-   `type`: The type of the application.
-   `repository`: The URL of the application's repository.
-   `build`: The command to build the application.
-   `start`: The command to start the application.

The `name`, `description`, and `type` fields are used to provide information about the application. The `repository` field is used to specify the URL of the repository that contains the application's code. The `build` and `start` fields are used to specify the commands to build and start the application.

Here is an example configuration file:

```
{
  "name": "My App",
  "description": "My App Description",
  "type": "webapp",
  "repository": "https://github.com/username/repo.git",
  "build": "npm run build",
  "start": "npm start"
}
```

### Deploying an Application

Once you have created the hosting configuration JSON file, you can deploy your application to Grams. To deploy the application, you will need to use the `grams deploy` command. This command will upload your application to IPFS and publish it to the Grams network.

### Updating an Application

To update an existing application, you can simply run the `grams deploy` command again with the updated hosting configuration JSON file.

## Grams Name Service

Grams provides a decentralized naming service that allows you to register a human-readable name for your application. This name can be used to access your application on the decentralized web, using the `grams://` protocol.

### Registering a Name

To register a name for your application, you will need to use the `grams name register` command. This command will register the name with the Grams Name Service and associate it with your application.

### Accessing Your Application

Once you have registered a name for your application, you can access it using the `grams://` protocol in any web browser that has the Grams browser extension installed. The extension will resolve the name to the IPFS hash of your application and load it in the browser.

## Conclusion

Hosting your web application on the decentralized web using Grams provides numerous benefits, including improved security, privacy, and accessibility. By taking advantage of the Grams hosting and naming services, you can easily deploy, update, and access your application on the decentralized web.
