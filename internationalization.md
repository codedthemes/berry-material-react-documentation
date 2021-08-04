---
description: 'Localization support IE11, Edge, Chrome, Firefox & Safari.'
---

# Internationalization

Berry supports four types of international languages \('**en**' - English, '**fr**' - French, '**ro**' - Romanian, '**zh**' - Chinese\). You can switch language from the header bar. We internationalize the main menu for all four languages, When you change it from the header, you will see the effect there. If you want to configure one more language or set a default language then continue reading below...

## How does it work?

Data for locale files exist at **`src\utils\locales`**

{% code title=".json file" %}
```javascript
{
    "dashboard": "Dashboard",
    "default": "Default",
    "analytics": "Analytics",
    ...
    ...
}
```
{% endcode %}

To change Locale, open file **`src\config.js`** file and set language

{% tabs %}
{% tab title="JavaScript" %}
{% code title="config.js" %}
```javascript
const config = {
    ...
    i18n: 'en', // 'en' - English, 'fr' - French, 'ro' - Romanian, 'zh' - Chinese
    ...
}
```
{% endcode %}
{% endtab %}

{% tab title="Typescript" %}
```typescript
import { PaletteMode } from '@material-ui/core';

const config: {
    ...
    i18n: string;
    ...    
    };
} = {
    ...
    // 'en' - English, 'fr' - French, 'ro' - Romanian, 'zh' - Chinese
    i18n: 'en',
    ...
};

export default config;

```
{% endtab %}
{% endtabs %}

Open file **`App.js`** and apply **IntlProvider**

{% tabs %}
{% tab title="JavaScript" %}
{% code title="App.js" %}
```javascript
import React from 'react';
import { useSelector } from 'react-redux';

import { ThemeProvider } from '@material-ui/core/styles';
import { CssBaseline, StyledEngineProvider } from '@material-ui/core';

// routing
import Routes from 'routes';

// defaultTheme
import themes from 'themes';

// project imports
import Locales from 'ui-component/Locales';
...
...

// ===========================|| APP ||=========================== //

const App = () => {
    const customization = useSelector((state) => state.customization);

    return (
        <StyledEngineProvider injectFirst>
            <ThemeProvider theme={themes(customization)}>
                <CssBaseline />
               ...
                <Locales>
                    ...
                </Locales>
               ...
            </ThemeProvider>
        </StyledEngineProvider>
    );
};

export default App;

```
{% endcode %}
{% endtab %}

{% tab title="Typescript" %}
```typescript
import { useSelector } from 'react-redux';

import { ThemeProvider } from '@material-ui/core/styles';
import { CssBaseline, StyledEngineProvider } from '@material-ui/core';

// routing
import Routes from 'routes';

// store
import { DefaultRootStateProps } from 'types';

// defaultTheme
import themes from 'themes';

// project imports
import Locales from 'ui-component/Locales';
...
...

// ==============================|| APP ||============================== //

const App = () => {
    const customization = useSelector((state: DefaultRootStateProps) => state.customization);

    return (
        <StyledEngineProvider injectFirst>
            <ThemeProvider theme={themes(customization)}>
                <CssBaseline />
               ...
                <Locales>
                    ...
                </Locales>
               ...
            </ThemeProvider>
        </StyledEngineProvider>
    );
};

export default App;

```
{% endtab %}
{% endtabs %}

