---
title: Create custom checkboxes and radios in Bootstrap
published: false
description: In this article, I will show you how we can change look and feel of checkboxes and radio buttons very easily using SCSS variables and functions.
tags: bootstrap,css,scss,ui
cover_image: https://dev-to-uploads.s3.amazonaws.com/i/mmuj3n0kdf9c9fvmes8o.png
---

# TL;DR

I have created a repo called [bootstrap-checkbox](https://github.com/shhdharmen/bootstrap-checkbox). You can simply get started from that, files to check for are: `src\styles\abstracts\_functions.scss`, `src\styles\abstracts\_variables.scss`, `src\styles\components\_checkbox.scss` and `src\styles\components\_radio.scss`.

# Bootstrap

[Bootstrap](https://getbootstrap.com/), I use it, you use and I guess every web developer must have used it in their career. In fact, according to [State of CSS 2019](https://2019.stateofcss.com/), Bootstrap is the framework which has most awareness among developers.

![Awareness, interest, and satisfaction ratio rankings. Note that these three ratios all correspond to the same point in time.](https://2019.stateofcss.com/images/captures/technologies_css-frameworks_tools-section-overview.png)

# Feature

I have used Bootstrap for last 4-5 years. The main feature that I look forward each time is, theming. By theming, I am not referring to only colors and typographics, I also need to change how buttons, checkboxes, radios, cards (and their shadows) look. Thanks to [Bootstrap's SASS](https://getbootstrap.com/docs/4.4/getting-started/theming/#sass) implementation, it has been really easy to achieve such things.

Let's talk business.

## Custom checkboxes and radios

We are going to use an existing project for this, which provides all the needed setup and functionalities to get started very quickly.

### 1. Fork the project and complete initial setup

So, first, fork [bootstrap-theme-kit](https://github.com/shhdharmen/bootstrap-theme-kit) repo and complete its [getting started guide](https://github.com/shhdharmen/bootstrap-theme-kit#-getting-started), now you've browser open at 3000 port.

### 2. HTML Content

You can simply replace all body content in html file, with below:

```html
<!-- keep head tag as it is -->
<body>
  <div class="container">
    <div class="col-sm-12 col-md-12 mb-5">
      <p class="text-gray">Checkbox</p>
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" id="customCheck1" />
        <label class="custom-control-label" for="customCheck1">Check this custom checkbox</label>
      </div>
      <div class="custom-control custom-checkbox mb-5">
        <input
          type="checkbox"
          class="custom-control-input"
          id="customCheck2"
          checked
        />
        <label class="custom-control-label" for="customCheck2">Or this one</label>
      </div>
      <p class="text-gray">Radios</p>
      <div class="custom-control custom-radio">
        <input
          type="radio"
          id="customRadio1"
          name="customRadio"
          class="custom-control-input"
          checked
        />
        <label class="custom-control-label" for="customRadio1">Toggle this custom radio</label>
      </div>
      <div class="custom-control custom-radio">
        <input
          type="radio"
          id="customRadio2"
          name="customRadio"
          class="custom-control-input"
        />
        <label class="custom-control-label" for="customRadio2">Or toggle this other custom radio</label>
      </div>
    </div>
  </div>
  <script type="text/javascript" src="js/bundle.js"></script>
</body>
```

### 3. Variables

This is very important.

Bootstrap handles everything through scss variables. So, to modify look and feel, we need to handle those variables in `src\styles\abstracts\_variables.scss`. Let's replace it's content:

```scss
// src\styles\abstracts\_variables.scss

// 1. Colors

$primary: #ea1c2b;
$white: #ffffff;
$dark: #000000;

// 2. Custom form control

$custom-control-indicator-size: 1.25rem;
$custom-control-indicator-border-color: $dark;
$custom-control-indicator-border-width: 0.125rem;
$custom-control-indicator-checked-color: $white;
$custom-control-indicator-checked-bg: $primary;
$custom-control-indicator-checked-border-color: $primary;
$custom-forms-transition: background-color 0.15s ease-in-out,
border-color 0.15s ease-in-out,
box-shadow 0.15s ease-in-out,
background-size 5s ease-in-out;

// 3. Checkbox
$custom-checkbox-indicator-border-radius: 0.125rem;
$custom-checkbox-indicator-icon-checked: str-replace(url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' %3e%3cpath fill='#{$custom-control-indicator-checked-color}' d='M21,7L9,19L3.5,13.5L4.91,12.09L9,16.17L19.59,5.59L21,7Z'/%3e%3c/svg%3e"),
    "#",
    "%23"
);

// 4. Radio

// 4.1 new variables
$custom-radio-indicator-icon-checked-color: $primary;
$custom-radio-checked-background-color: $white;

$custom-radio-indicator-icon-checked: url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='-4 -4 8 8'><circle r='3' fill='#{$custom-radio-indicator-icon-checked-color}'/></svg>");
```

# Credits

Generated using [Bootstrap theme kit](https://shhdharmen.github.io/bootstrap-theme-kit/).
