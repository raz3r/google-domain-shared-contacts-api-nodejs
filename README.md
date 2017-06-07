# Google Domain Shared Contacts API

An unofficial **work in progress** library that allows to list, create, delete and update Google Domain Shared Contacts. The library uses JWT and Service Accounts for authentication. Follow the [official guide](https://developers.google.com/admin-sdk/directory/v1/guides/delegation) and create a Service Account with Domain Wide Delegation (DWD) if you haven't done so yet.

## Install

````
npm install COMING SOON
````

## Dependencies

* googleapis - Google APIs JWT authentication is used to grant permissions to the application.
* request - Request is used to make HTTP requests to the Shared Contacts feed.
* xmlbuilder - Shared Contacts API can output JSON but only accept XML when doing specific tasks such as creating or updating entries.

## Usage

First import the library and configure JWT parameters. The [googleapis](https://github.com/google/google-api-nodejs-client/blob/master/samples/jwt.js) documentation explains how to configure JWT in details.

```javascript
var sharedcontacts = require('google-domain-shared-contacts-api')({
	email : 'Your Service Account Email, ie xxx@iam.gserviceaccount.com',
	keyFile : 'Path to your PEM Key File, ie ./key.pem',
	key : null,
	scopes : [ 'https://www.google.com/m8/feeds' ],
	delegate : 'The email address of an user in the domain with Admin rights, ie administrator@example.com',
	domain : 'Your domain, ie example.com'
});
```

The library exposes four methods which allow to list, create, delete and update Shared Contacts. All methods and their parameters are explained in details in the [library code](sharedcontacts.js).

For instance to list all Shared Contacts that contain the word 'Test' and output the results in JSON format you can do the following.

```javascript
sharedcontacts.list({
    alt : 'json',
    q : 'Test'
  },function(error, response, body) {
    if (error) {
      // Handle the error
    }
    else {
      // Handle the response/body
    }
});
```

## Disclaimer

This library requires a DWD Service Account in order to interact with Shared Contacts API, if you're not familiar with the argument please restrain from using this library. The author does not take any responsibility for any harm done to the data in your Google Apps domain.

**This library is not sponsored, supported, or affiliated with Google.**
