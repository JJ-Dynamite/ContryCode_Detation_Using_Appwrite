# ContryCode_Detation_Using_Appwrite
Appwrite provides a [Location API](https://appwrite.io/docs/location) that allows you to get information about the user's location based on their IP address. You can use this API to get the user's country code without using a third-party geocoding API.

Here's an example of how you can use the Appwrite Location API to get the user's country code using an Appwrite Cloud Function:

```javascript
const sdk = require("node-appwrite");

// Initialize the Appwrite SDK
const client = new sdk.Client();
client
  .setEndpoint(process.env.APPWRITE_ENDPOINT)
  .setProject(process.env.APPWRITE_PROJECT_ID)
  .setKey(process.env.APPWRITE_API_KEY);

// Use the Appwrite Location API to get the user's country code
const location = new sdk.Location(client);
location.get().then((response) => {
  const countryCode = response.countryCode;
  console.log(`Country code: ${countryCode}`);
});
```

In this example, we use the `node-appwrite` SDK to initialize the Appwrite client. We then use the `get` method of the `Location` class to get information about the user's location based on their IP address. The response includes the user's country code, which we can access using the `countryCode` property.

You can trigger this function from your app to get the user's country code. For example:

```javascript
const sdk = require("node-appwrite");

// Initialize the Appwrite SDK
const client = new sdk.Client();
client
  .setEndpoint("https://[HOSTNAME_OR_IP]/v1")
  .setProject("YOUR_PROJECT_ID")
  .setKey("YOUR_API_KEY");

// Trigger the Appwrite function
const functions = new sdk.Functions(client);
const response = await functions.createExecution("YOUR_FUNCTION_ID");
console.log(response);
```

In this example, we use the `createExecution` method of the `Functions` class to trigger the Appwrite function.

