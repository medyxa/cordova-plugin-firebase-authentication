# cordova-plugin-firebase-authentication<br>[![NPM version][npm-version]][npm-url] [![NPM downloads][npm-downloads]][npm-url]
> Cordova plugin for [Firebase Authentication](https://firebase.google.com/docs/auth/)

## Installation

    cordova plugin add cordova-plugin-firebase-authentication --save

If you need to set a specific dependency version on Android then use variable `FIREBASE_VERSION`.

To use phone number authentication on iOS, your app must be able to receive silent APNs notifications from Firebase. For iOS 8.0 and above silent notifications do not require explicit user consent and is therefore unaffected by a user declining to receive APNs notifications in the app. Thus, the app does not need to request user permission to receive push notifications when implementing Firebase phone number auth.

## Supported Platforms

- iOS
- Android

## Methods
Every method call returns a promise which is optionally fulfilled with an appropriate value.

### getIdToken(_forceRefresh_)
Returns a JWT token used to identify the user to a Firebase service.
```js
cordova.plugins.firebase.auth.getIdToken().then(function(idToken) {
    // send token to server
});
```

### signInWithEmailAndPassword(_email_, _password_)
Asynchronously signs in using an email and password.
```js
cordova.plugins.firebase.auth.signInWithEmailAndPassword("my@mail.com", "pa55w0rd").then(function(userInfo) {
    // user is signed in
});
```

### verifyPhoneNumber(_phoneNumber_)
Starts the phone number verification process for the given phone number.
```js
cordova.plugins.firebase.auth.verifyPhoneNumber("+123456789").then(function(verificationId) {
    // pass verificationId to signInWithVerificationId
});
```

### signInWithVerificationId(_verificationId_, _smsCode_)
Asynchronously signs in using verificationId and 6-digit SMS code.
```js
cordova.plugins.firebase.auth.signInWithVerificationId("djgfioerjg34", "123456").then(function(userInfo) {
    // user is signed in
});
```

### signOut()
Signs out the current user and clears it from the disk cache.
```js
cordova.plugins.firebase.auth.signOut().then(function() {
    // user was signed out
});
```

[npm-url]: https://www.npmjs.com/package/cordova-plugin-firebase-authentication
[npm-version]: https://img.shields.io/npm/v/cordova-plugin-firebase-authentication.svg
[npm-downloads]: https://img.shields.io/npm/dt/cordova-plugin-firebase-authentication.svg

