---
description: Defines core of theme. How theme is being set using Material-UI.
---

# Theme/Style Configuration

Customize Berry with your theme. You can change the colors, the typography, and much more. Material-UI provides flexibility to change the style of the project in a single place and on top of it, we made it more centralize and consistent by proper file structure.

## Theme configuration

The whole theme can be configured from the folder **`..\src\themes`** . Theme initialization starts in **`index.js`**, where palette, typography, and component's overridable style exist.

{% tabs %}
{% tab title="JavaScript" %}
{% code title="index.js" %}
```javascript
import { createTheme } from '@material-ui/core/styles';

// assets
import colors from 'assets/scss/_themes-vars.module.scss';
import theme1 from 'assets/scss/_theme1.module.scss';
import theme2 from 'assets/scss/_theme2.module.scss';
import theme3 from 'assets/scss/_theme3.module.scss';
import theme4 from 'assets/scss/_theme4.module.scss';
import theme5 from 'assets/scss/_theme5.module.scss';
import theme6 from 'assets/scss/_theme6.module.scss';

// project imports
import componentStyleOverrides from './compStyleOverride';
import themePalette from './palette';
import themeTypography from './typography';
import customShadows from './shadows';

/**
 * Represent theme style and structure as per Material-UI
 * @param {JsonObject} customization customization parameter object
 */
export function theme(config) {
    let color;
    switch (config.presetColor) {
        case 'theme1':
            color = theme1;
            break;
        case 'theme2':
            color = theme2;
            break;
        case 'theme3':
            color = theme3;
            break;
        case 'theme4':
            color = theme4;
            break;
        case 'theme5':
            color = theme5;
            break;
        case 'theme6':
            color = theme6;
            break;
        case 'default':
        default:
            color = colors;
    }

    const themeOption = {
        ...
        paper: '',
        ...
    };

    switch (config.navType) {
        case 'dark':
            themeOption.paper = color.darkLevel2;
            ...
            break;
        case 'light':
        default:
            themeOption.paper = color.paper;
            ...
            break;
    }

    return createTheme({
        direction: config.rtlLayout ? 'rtl' : 'ltr',
        palette: themePalette(themeOption),
        mixins: {
            toolbar: {
                minHeight: '48px',
                padding: '16px',
                '@media (min-width: 600px)': {
                    minHeight: '48px'
                }
            }
        },
        breakpoints: {
            values: {
                xs: 0,
                sm: 600,
                md: 960,
                lg: 1280,
                xl: 1920
            }
        },
        typography: themeTypography(themeOption),
        customShadows: customShadows(config.navType, themeOption),
        components: componentStyleOverrides(themeOption)
    });
}

export default theme;
```
{% endcode %}
{% endtab %}

{% tab title="Typescript" %}
```typescript
import { createTheme } from '@material-ui/core/styles';

// assets
import colors from 'assets/scss/_themes-vars.module.scss';
import theme1 from 'assets/scss/_theme1.module.scss';
import theme2 from 'assets/scss/_theme2.module.scss';
import theme3 from 'assets/scss/_theme3.module.scss';
import theme4 from 'assets/scss/_theme4.module.scss';
import theme5 from 'assets/scss/_theme5.module.scss';
import theme6 from 'assets/scss/_theme6.module.scss';

// project imports
import componentStyleOverrides from './compStyleOverride';
import themePalette from './palette';
import themeTypography from './typography';
import customShadows from './shadows';
import { ColorProps, CustomizationStateProps } from 'types';

/**
 * Represent theme style and structure as per Material-UI
 * @param {JsonObject} customization customization parameter object
 */

export const theme = (customization: CustomizationStateProps) => {
    let color: ColorProps;
    switch (customization.presetColor) {
        case 'theme1':
            color = theme1;
            break;
        case 'theme2':
            color = theme2;
            break;
        case 'theme3':
            color = theme3;
            break;
        case 'theme4':
            color = theme4;
            break;
        case 'theme5':
            color = theme5;
            break;
        case 'theme6':
            color = theme6;
            break;
        case 'default':
        default:
            color = colors;
    }

    const themeOption = {
        ...
        paper: '',
        ...
    };

    switch (customization.navType) {
        case 'dark':
            themeOption.paper = color.darkLevel2;
            ...
            break;
        case 'light':
        default:
            themeOption.paper = color.paper;
            ...
            break;
    }

    return createTheme({
        direction: customization.rtlLayout ? 'rtl' : 'ltr',
        palette: themePalette(themeOption),
        mixins: {
            toolbar: {
                minHeight: '48px',
                padding: '16px',
                '@media (min-width: 600px)': {
                    minHeight: '48px'
                }
            }
        },
        breakpoints: {
            values: {
                xs: 0,
                sm: 600,
                md: 960,
                lg: 1280,
                xl: 1920
            }
        },
        typography: themeTypography(themeOption),
        customShadows: customShadows(customization.navType, themeOption),
        components: componentStyleOverrides(themeOption)
    });
};

export default theme;
```
{% endtab %}
{% endtabs %}

As you can see colors for the theme came from the central location **`import value from '../assets/scss/_themes-vars.module.scss';`**

{% tabs %}
{% tab title=":themes-vars.module.scss" %}
```css
// paper & background
$paper: #ffffff;

// primary
$primaryLight: #e3f2fd;
...

// secondary
$secondaryLight: #ede7f6;
...

// success Colors
$successLight: #b9f6ca;
...

// error
$errorLight: #ef9a9a;
...

// orange
$orangeLight: #fbe9e7;
...

// warning
$warningLight: #fff8e1;
...

// grey
$grey50: #fafafa;
...

//-----------------------|| DARK THEME VARIANTS ||-----------------------//

// paper & background
$darkBackground: #1a223f; // level 3
$darkPaper: #111936; // level 4

// dark 800 & 900
$darkLevel1: #29314f; // level 1
$darkLevel2: #212946; // level 2

// primary dark
$darkPrimaryLight: #e3f2fd;
...

// secondary dark
$darkSecondaryLight: #d1c4e9;
...

// text variants
$darkTextTitle: #d7dcec;
...

//-----------------------|| JAVASCRIPT ||-----------------------//

:export {
    // paper & background
    paper: $paper;

    // primary
    primaryLight: $primaryLight;
    primary200: $primary200;
    primaryMain: $primaryMain;
    primaryDark: $primaryDark;
    primary800: $primary800;

    // secondary
    secondaryLight: $secondaryLight;
    secondary200: $secondary200;
    secondaryMain: $secondaryMain;
    secondaryDark: $secondaryDark;
    secondary800: $secondary800;

    // success
    successLight: $successLight;
    success200: $success200;
    successMain: $successMain;
    successDark: $successDark;

    // error
    errorLight: $errorLight;
    errorMain: $errorMain;
    errorDark: $errorDark;

    // orange
    orangeLight: $orangeLight;
    orangeMain: $orangeMain;
    orangeDark: $orangeDark;

    // warning
    warningLight: $warningLight;
    warningMain: $warningMain;
    warningDark: $warningDark;

    // grey
    grey50: $grey50;
    grey100: $grey100;
    grey200: $grey200;
    grey300: $grey300;
    grey500: $grey500;
    grey600: $grey600;
    grey700: $grey700;
    grey900: $grey900;

    //-----------------------|| DARK THEME VARIANTS ||-----------------------//

    // paper & background
    darkPaper: $darkPaper;
    darkBackground: $darkBackground;

    // dark 800 & 900
    darkLevel1: $darkLevel1;
    darkLevel2: $darkLevel2;

    // text variants
    darkTextTitle: $darkTextTitle;
    darkTextPrimary: $darkTextPrimary;
    darkTextSecondary: $darkTextSecondary;

    // primary dark
    darkPrimaryLight: $darkPrimaryLight;
    darkPrimaryMain: $darkPrimaryMain;
    darkPrimaryDark: $darkPrimaryDark;
    darkPrimary200: $darkPrimary200;
    darkPrimary800: $darkPrimary800;

    // secondary dark
    darkSecondaryLight: $darkSecondaryLight;
    darkSecondaryMain: $darkSecondaryMain;
    darkSecondaryDark: $darkSecondaryDark;
    darkSecondary200: $darkSecondary200;
    darkSecondary800: $darkSecondary800;
}
```
{% endtab %}
{% endtabs %}

You can check other settings like theme typography, palette, and components style override in the same folder. **`..src\themes`**

### How to customize it?

You might come across questions like how to change a theme's **primary** color? How to change textbox or other components which can apply to an entire theme?

#### Customize Theme Colors

To change the color of the theme, you can either apply color directly to `..src\theme\palatte.js` **or** defines a new variable in `..src\assets\scss\_themes-vars.module.scss` and replace it in `palatte.js`

For instance, if you want to change color where `theme.palette.primary.light` is being used in a theme then, update following in **`..src\themes\palatte.js`**

{% code title="palatter.js" %}
```javascript
import value from '../assets/scss/_themes-vars.module.scss';

/**
 * Color intention that you want to used in your theme
 */
export function themePalatte(theme) {
    return {
        ...
        primary: {
            light: '#fff000', // change this to your desired color
            ...
        },
        ...
        ...

    };
}
```
{% endcode %}

#### Customize Theme Typography

You can customize the typography used in the theme as well from the central place.

For instance, If you want to change `font-weight` of the typography `h5` to `900`. To do that, open **`..src\themes\typography.js`** and update as below:

{% code title="typography.js" %}
```javascript
/**
 * Typography used in theme
 */
export function themeTypography(theme) {
    return {
        ...
        h5: {
            ...
            fontWeight: 900 // changed this to make it 900 from 500
        },
        ...
    };
}
```
{% endcode %}

This will apply to all places where you used Typography variants as **`h5`**

**`<Typography variant="h5"...>`**

#### Customize MUI Component style

We have provided a central location to override any default style of any component. All the overrides styles exist in **`src\themes\compStyleOverride.js`**

{% code title="compStyleOverride.js" %}
```javascript
import value from '../assets/scss/_themes-vars.module.scss';

/**
 * MUI Componets whose styles are overrided as per theme
 */
export function componentStyleOverrides(theme) {
    return {
        MuiButton: {
            styleOverrides: {
                root: {
                    fontWeight: 500,
                    textTransform: 'capitalize',
                    borderRadius: '4px'
                }
            }
        },
        ...
        ...
        MuiDialog: {
            styleOverrides: {
                paper: {
                    padding: '12px 0 12px 0'
                }
            }
        }
    };
}
```
{% endcode %}

You can add default property for any MUI component and it will be applied everywhere. We emitted lines to view it better in the above code block but you can see many controls' styles override in the same file. Feel free to change it as per your need.
