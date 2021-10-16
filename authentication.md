---
description: Auth0, JWT, Firebase setup
---

# Authentication

Berry includes three Authentication methods **`Firebase, JSON Web Token (JWT), Auth0`** for their users. Users can change it as per their needs.

{% hint style="info" %}
Firebase Authentication is set by default
{% endhint %}

{% embed url="https://youtu.be/daHRKlIi6Uc?list=PLknn3jaIuWiDKKEy3EO-p5-MP1nSOgUr1" %}
Authentication
{% endembed %}

## How does it work?

Only authenticated users can access dashboard pages. If a user is not authenticated, the user is redirected to the login page.

We used two guards **`GuestGuard`** and **`AuthGuard.`** Guards have been configured in **`src\utils\route-guard\`** folder.

In the **`src/layout/App.js`**, we have specified auth provider **`FirebaseProvider`** like,

{% code title="App.js" %}
```javascript
import { FirebaseProvider } from "../contexts/FirebaseContext";
```
{% endcode %}

App component wrap with the **`<FirebaseProvider>`**

```javascript
<ThemeProvider theme={theme(customization)}>
  ...
  <FirebaseProvider>
    <Routes />
    <Snackbar />
  </FirebaseProvider>
  ...
</ThemeProvider>
```

Using **`<FirebaseProvider>`**, we can use the context directly by importing **`useContext`** from React and specifying the context **`FirebaseContext`** or we can use the custom hook **`useAuth`** from `src/hooks/useAuth.js`

## Auth Configuration:

All configurations related to authentication are stored in config.js. Those configs are like APIKey to connect authentication server, project id, etc.

{% hint style="danger" %}
Berry has a dummy/test config to make authentication works. Users have to change api and secret as per their project need. One should not use those provided keys in their live environment.
{% endhint %}

{% code title="config.js" %}
```javascript
// JWT JSON Web Token method
jwt: {
    secret: 'SECRET-KEY',
    timeout: '1 days'
},

// Firebase Authentication method
firebase: {
    apiKey: "API-KEY",
    authDomain: "AUTH-DOMAIN",
    databaseURL: "DATABASE-URL",
    projectId: "PROJECT-ID",
    storageBucket: "STORAGE-BUCKET",
    messagingSenderId: "MESSAGEING-SENDER-ID",
    appId: "APP-ID",
    measurementId: "MEASUREMENT-ID"
},

// Auth0 method
auth0: {
    client_id: 'CLIENT-ID',
    domain: 'DOMAIN'
}
```
{% endcode %}

> The theme provides working an example for Login and Register only. Other flow like reset password, verification have to make it workable by the user himself.

## Switching between Authentication methods

### **Firebase to Auth0**

**Set Auth0 Config**

At present, Auth0 uses a dummy client id and domain, so we don't need to change anything, but in actual implementation, you need to set client id and domain in the following file. For more detail refer to Auth0 here: [https://auth0.com/docs/get-started/auth0-overview](https://auth0.com/docs/get-started/auth0-overview)

{% code title="..\src\config.js" %}
```javascript
...
  auth0: {
        client_id: 'This is dummy id',
        domain: 'this.is.dummy.domain'
    }
...
```
{% endcode %}

**Change AuthProvider**

{% code title="..\src\App.js" %}
```javascript
import { Auth0Provider } from 'contexts/Auth0Context';

// Also find & edit below code block
<Auth0Provider>
    <Routes />
    <Snackbar />
</Auth0Provider>
```
{% endcode %}

**Change auth Hooks**

Comment another context in the following file and uncomment Auth0 one.

{% code title="..\src\hooks\useAuth.js" %}
```javascript

import AuthContext from 'contexts/Auth0Context';
```
{% endcode %}

#### Copy login code

It's super simple. We have provided a code that just needs to be replaced. Copy code from `src\views\pages\authentication\login\Auth0Login` and replace it entirely to `src\views\pages\authentication\auth-forms\AuthLogin.tsx`

#### Copy register code

We have provided a code that just needs to be replaced. Copy code from `src\views\pages\authentication\login\Auth0Register` and replace it to `src\views\pages\authentication\auth-forms\AuthRegister.tsx`

### **Firebase to **JWT

**Set JWT Config**

At present, jwt uses a dummy backend call, so we don't need any secret, but in actual implementation, you need to set a secret in the following file. For more detail refer to JWT here: [https://jwt.io/introduction](https://jwt.io/introduction)

{% code title="..\src\config.js" %}
```javascript
...
  jwt: {
      secret: 'SECRET-KEY',
      timeout: '1 days'
  }
...
```
{% endcode %}

**Change AuthProvider**

{% code title="..\src\App.js" %}
```javascript
// Replace at line 6:
import { JWTProvider } from "./contexts/JWTContext";

// Also find & edit below code block
<JWTProvider>
    <Routes />
    <Snackbar />
</JWTProvider>
```
{% endcode %}

**Change auth Hooks**

Comment another context in the following file and uncomment JWT one.

{% code title="..\src\hooks\useAuth.js" %}
```javascript
import AuthContext from 'contexts/JWTContext';
```
{% endcode %}

#### Copy login code

It's also super simple. We have provided a code that just needs to be replaced. Copy code from `src\views\pages\authentication\login\JWTLogin` and replace it entirely to `src\views\pages\authentication\auth-forms\AuthLogin.tsx`

#### Copy register code

We have provided a code that just needs to be replaced. Copy code from `src\views\pages\authentication\login\JWTRegister` and replace it to `src\views\pages\authentication\auth-forms\AuthRegister.tsx`
