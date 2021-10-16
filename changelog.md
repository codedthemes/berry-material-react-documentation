---
description: Defines change log
---

# Changelog

## v3.0.0 - (20-10-2021)

* Migration to M-UI 5.0.3 stable version (Major change)
* Kanban App
* Simplified Authentication flow
* Upgrade react-router package
* Other improvements like styling, documentation, etc
* Added new tutorial videos for documentation
  * How to Video series
  * Authentication Video

### Migration From v2.0.0 to v3.0.0

Major changes in this version are to migrate the latest MUI stable version. withStyle and makeStyle are no longer supported. So if you wanna migrate your project to latest stable version, you can do two things.

1. Run CodeMode by M-UI
   * [https://mui.com/guides/migration-v4](https://mui.com/guides/migration-v4)
2. Compare style with v3.0.0 and move it to your code

## v2.0.0 - (03-08-2021)

* Upgrade to Material-UI Beta: 5.0.0-beta.1
* Upgrade to react-router: 6.0.0-beta.0
* [E-Commerce](https://berrydashboard.io/e-commerce/products) App
  * Product List
  * Product Details
  * Checkout
* Enforce Eslint Rules
* Absolute imports
* Remove package "react-material-UI-carousel" due to no support in MUI Beta. Achieved same using "slick-carousel"
* Other minor improvements & fixes

### Migration From v1.2.0 to v2.0.0

#### Use Codemods for Material-UI upgrades

Material-UI provides `codemods` \*\*\*\*for migration. Please follow this guideline: [https://next.material-ui.com/guides/migration-v4/#run-codemods](https://next.material-ui.com/guides/migration-v4/#run-codemods) We highly recommend checking the above link if you want to upgrade your current project.

#### react-router upgrades

Follow this if you want to use react-router beta: [https://github.com/ReactTraining/react-router/blob/dev/docs/advanced-guides/migrating-5-to-6.md](https://github.com/ReactTraining/react-router/blob/dev/docs/advanced-guides/migrating-5-to-6.md)

## v1.2.0 - (12-06-2021)

**Added**

* [Form Layouts](https://berrydashboard.io/forms/layouts/layouts)
  * Multiple layouts - Simple, Horizontal, with label, divider
  * Multi column forms
  * Action bar
  * Sticky Action bar
* [Form Validation](https://berrydashboard.io/forms/forms-validation)
* [Form Wizard](https://berrydashboard.io/forms/forms-wizard)
* Theme
  * 6 color preset files
  * [Grid](https://berrydashboard.io/utils/util-grid) page
* [Animation](https://berrydashboard.io/utils/util-animation)
* [Button](https://berrydashboard.io/components/button) color shadows & Animation

**Fixes**

* Added color preset files.
* Authentication responsive issues fixed.
* Change color variables name
* Table->Enhanced Table checkbox issue fixed.
* Pricing pages fixed.
* Set 404 Error page redirection.

**Apps**

* Mail
  * Change the structure of the Mail app
  * Fixed responsive issues.
* Chat
  * Fixed responsive issue.
  * The drawer issue is fixed.

### Migration from v1.1.0 to v1.2.0

#### Change in naming of color variable to make theme scalable for multiple color options.

| Old               | New               |
| ----------------- | ----------------- |
| blue50            | primaryLight      |
| blue200           | primary200        |
| blue500           | primaryMain       |
| blue600           | primaryDark       |
| blue800           | primary800        |
| deepPurple50      | secondaryLight    |
| deepPurple200     | secondary200      |
| deepPurple500     | secondaryMain     |
| deepPurple600     | secondaryDark     |
| deepPurple800     | secondary800      |
| A100              | successLight      |
| A200              | success200        |
| A400              | successMain       |
| A700              | successDark       |
| red200            | errorLight        |
| red500            | errorMain         |
| red800            | errorDark         |
| deepOrange50      | orangeLight       |
| deepOrange200     | orangeMain        |
| deepOrange800     | orangeDark        |
| amber50           | warningLight      |
| amber100          | warningMain       |
| amber500          | warningDark       |
| backgroundDark    | darkBackground    |
| paperDark         | darkPaper         |
| textDarkTitle     | darkTextTitle     |
| textDarkPrimary   | darkTextPrimary   |
| textDarkSecondary | darkTextSecondary |

## v1.1.0 - (28-05-2021)

* More closer to the single responsibility model
* Added propTypes declaration for components which helps in the development
* Set Prettier formatting property "bracketSpacing" as `true` for better readability
* Code clean up and minor bug fixes
* File Restructured for better code understanding
* Code commenting and documentation

{% hint style="warning" %}
If you using v1.0, please do backup your files first.
{% endhint %}

## v1.0 - Release (15-05-2021)

* Berry initial release
