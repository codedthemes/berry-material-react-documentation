---
description: How to change available color presets
---

# Color Presets

Berry come up with 6+ theme color presets. You can now change the available color presets by doing the following steps:

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
{% tab title="javascript" %}
```javascript
const config = {
    ...
    presetColor: 'default', // default, theme1, theme2 to theme6 available
    ...
    ...
    ...
}
```
{% endtab %}

{% tab title="typescript" %}
```typescript
import { PaletteMode } from '@material-ui/core';

const config: {
    ...
    theme: PaletteMode;
    ...
} = {
    ...
    presetColor: 'default', // default, theme1, theme2, theme3 upto theme6
    ...
};

export default config;

```
{% endtab %}
{% endtabs %}



