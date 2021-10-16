---
description: Page and URL routing
---

# Routing

Berry routing system is based on [react-router](https://reacttraining.com/react-router/) and its package [react-router-dom,](https://reacttraining.com/react-router/web/guides/quick-start) it's also using code splitting for better performance.

{% hint style="info" %}
**How can I add a new page with a menu item?**

You can use the below explanation to add/remove menu routes and their menu items.
{% endhint %}

## Configure route

Open `...\src\routes\index.js` You will find the below example code. In the below code we have shown four different routes. **`<MainRoutes/>`** is the main layout routing you see after login.

{% tabs %}
{% tab title="Javascript" %}
```javascript
...
...

// ===============|| ROUTING RENDER ||=================== //

export default function ThemeRoutes() {
    return useRoutes([
        { path: '/', element: <PagesLanding /> }, 
        AuthenticationRoutes, 
        LoginRoutes, 
        MainRoutes]);
}
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
...
...

// ===============|| ROUTING RENDER ||=================== //

export default function ThemeRoutes() {
    return useRoutes([
        { path: '/', element: <PagesLanding /> }, 
        AuthenticationRoutes, 
        LoginRoutes, 
        MainRoutes]);
}
```
{% endtab %}
{% endtabs %}

### Add New menu/route in the main layout

To add one more menu item in **`<MainRoutes />`**, update the following file at the same location **`...\src\routes\MainRoutes.js`**

{% tabs %}
{% tab title="JavaScript" %}
{% code title="MainRoutes.js" %}
```javascript
...
...
const SamplePage = Loadable(lazy(() => import('views/sample-page')));
// import new view and save it in constant. for e.g
const NewMenu = Loadable(lazy(() => import('views/new-menu')));

const MainRoutes = {
    path: '/',
    element: (
        <AuthGuard>
            <MainLayout />
        </AuthGuard>
    ),
    children: [
        {
            path: '/sample-page',
            element: <SamplePage />
        },
        {
            path: '/newmenu',
            element: <NewMenu />
        }
    ]
};

export default MainRoutes;
```
{% endcode %}
{% endtab %}

{% tab title="Typescript" %}
```typescript
...
...
const SamplePage = Loadable(lazy(() => import('views/sample-page')));
// import new view and save it in constant. for e.g
const NewMenu = Loadable(lazy(() => import('views/new-menu')));

const MainRoutes = {
    path: '/',
    element: (
        <AuthGuard>
            <MainLayout />
        </AuthGuard>
    ),
    children: [
        {
            path: '/sample-page',
            element: <SamplePage />
        },
        {
            path: '/newmenu',
            element: <NewMenu />
        }
    ]
};

export default MainRoutes;
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Any route added in **`<MainLayout>`** will automatically go through **\<AuthGuard>**
{% endhint %}
