---
description: How to change available color presets i.e. available from v1.2.0
---

# Color Presets

Berry come up with 6+ theme color presets. You can now change the available color presets by doing following steps

Color Preset files are available in **`src\assets\scss\`** directory.

{% tabs %}
{% tab title="src\\assets\\scss\\" %}
```
..
├── _theme1.module.scss
├── _theme2.module.scss
├── ..
├── ..
├── ..
├── _theme6.module.scss
```
{% endtab %}
{% endtabs %}

Edit & Choose your desire preset color setting in **`src\config.js`** file. Change the **`presetColor`** value to `theme1, theme2 to theme6`

**`presetColor: theme1`**

{% tabs %}
{% tab title="config.js" %}
```javascript
const config = {
    basename: '',
    defaultPath: '/dashboard/default',
    fontFamily: `'Roboto', sans-serif`,
    borderRadius: 12,
    outlinedFilled: true,
    theme: 'light',
    presetColor: 'default', // default, theme1, theme2 to theme6 available
    
    ...
    ..
    .
```
{% endtab %}
{% endtabs %}



