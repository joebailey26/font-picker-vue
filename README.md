# Font Picker for Vue

**A simple, customizable font picker allowing users to preview, select, and use Google Fonts on your website.**

* Automatic font download and generation of the required CSS styles
* Efficient font previews (previews are loaded dynamically and full fonts are only downloaded on selection)

→ **[Demo](https://samuelmeuli.github.io/font-picker)**

_This is the Vue component for the [**Font Picker**](https://github.com/samuelmeuli/font-picker) package._

<p align="center">
  <img src=".github/demo.gif" width=700 alt="Demo">
</p>


## Getting started

### 1. Setup

Install the package using **NPM**:

```sh
npm install https://github.com/joebailey26/font-picker-vue
```


### 2. Displaying the font picker

Import the **`<font-picker>` component** to your Vue code:

```javascript

import Vue from 'vue';
import FontPicker from 'font-picker-vue';

Vue.use(FontPicker);
```

Use the component:

```html
<font-picker :api-key="'YOUR-KEY-HERE'" :options="options" :active-font="fontFamily" @change="myFunc"></font-picker
```

### 3. Applying the selected font

**Add `class="apply-font"` to all elements you want to apply the selected font to.**

When the user selects a font, it will automatically be downloaded and applied to all HTML elements of the `"apply-font"` class.


## Customization

The following **props** can be passed to the `FontPicker` component:

* **`apiKey` (required)**: Google API key (can be generated [here](https://developers.google.com/fonts/docs/developer_api#APIKey))
* **`activeFont`**: Font that should be selected in the font picker and applied to the text (default: `'Open Sans'`). Must be stored in component state, and be updated using an `onChange` listener
* **`options`**: Object with additional (optional) parameters:
  * **`name`**: If you have multiple font pickers on your site, you need to give them unique names (which may only consist of letters and digits). These names must also be appended to the font picker's ID and the `.apply-font` class name; e.g. if `{ name: 'main' }`, use `#font-picker-main` and `.apply-font-main`
  * **`families`**: If only specific fonts shall appear in the list, specify their names in an array (default: all font families)
  * **`categories`**: Array of font categories – possible values: `'sans-serif', 'serif', 'display', handwriting', 'monospace'` (default: all categories)
  * **`variants`**: Array of variants which the fonts must include and which will be downloaded; the first variant in the array will become the default variant (and will be used in the font picker and the `.apply-font` class); e.g. `['regular', 'italic', '700', '700italic']` (default: `['regular']`)
  * **`limit`**: Maximum number of fonts to be displayed in the list (the least popular fonts will be omitted; default: `100`)
  * **`sort`**: Sorting attribute for the font list – possible values: `'alphabetical'` (default), `'popularity'`
* **`onChange`**: Function which is executed whenever the user changes the active font and its stylesheet finishes downloading
