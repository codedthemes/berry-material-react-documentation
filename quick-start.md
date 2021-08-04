---
description: Quick start your project using Berry.
---

# Quick Start

{% embed url="https://youtu.be/u7xAjqjp4fU?list=PLknn3jaIuWiDKKEy3EO-p5-MP1nSOgUr1" caption="Build and deploy berry" %}

> If you prefer reading docs, continue reading below instead watching video.

### Installation

Navigate to your root folder **`(i.e. berry-material-react)`**

```text
c:\>cd berry-material-react
```

Install Packages by **npm** or **yarn** as per your preferences. Here we are using **`yarn`** package manager.

```bash
c:\berry-material-react> yarn
```

### Start

After package installation, you can start your app by using **`yarn start`** command

```bash
c:\berry-material-react> yarn start
```

This will start your local server at **`http://localhost:3000`** Also, your terminal shows the following.

```javascript
Compiled successfully!

You can now view berry-material-react in the browser.

Local:            http://localhost:3000    
On Your Network:  http://192.168.29.77:3000

Note that the development build is not optimized.
To create a production build, use yarn build.
```

### Build & Deploy

This might be too early to deploy but it is always good to know how to deploy.

To build your app in production use **`yarn build`** command

```javascript
c:\berry-material-react> yarn build
or
c:\berry-material-react> npm run build
```

### Deploy for your live site

Change the base URL with your domain and build your application.

You can control this with the `homepage` field in your **`package.json`**

{% code title="package.json" %}
```javascript
"homepage" : "http://example.com"
```
{% endcode %}

{% hint style="danger" %}
Deploying to subdirectory is stopped after migrating to 6.0.0-beta.0 of react-route. Watch this issue for more: [https://github.com/ReactTraining/react-router/issues/7216](https://github.com/ReactTraining/react-router/issues/7216)
{% endhint %}

{% hint style="info" %}
**You’ll need to have Node v12.x.x or later on your local development machine** \(but it’s not required on the server\). You can use [nvm](https://github.com/creationix/nvm#installation) \(macOS/Linux\) or [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) to easily switch Node versions between different projects.
{% endhint %}

