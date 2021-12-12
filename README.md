## Bootstrap Customize By scss
- Auto Run Live Scss Compiler (Settings > Live Scss Compiler > settings.json)

```
"liveServer.settings.donotShowInfoMsg": true,
"liveServer.settings.donotVerifyTags": true,
"liveSassCompile.settings.generateMap": false,
"liveSassCompile.settings.formats": [
    {
        "format": "expanded",
        "extensionName": ".css",
        "savePath": "/css"
    },
    {
        "format": "compressed",
        "extensionName": ".min.css",
        "savePath": "/css"
    }
],
```

- SCSS File Import
```
/* Custom Color */
$primary: #c29938;

/* Media query Break Point */
/* $grid-breakpoints: (
  xs: 0,
  sm: 576px,
  md: 768px,
  lg: 992px,
  xl: 1200px,
  xxl: 1400px
); */

/* Container Max Width */
$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1040px,
  xxl: 1224px
);

/* Number of Columns */
$grid-columns: 120;
$grid-gutter-width: 20px;
$grid-row-columns: 60;

/* Import Bootstrap */
@import '../node_modules/bootstrap/scss/bootstrap.scss';
```

- * Adding New Color:(Above of Bootstrap Import)
```
//Import Function and Variable
@import '../node_modules/bootstrap/scss/functions';
@import '../node_modules/bootstrap/scss/variables';
@import '../node_modules/bootstrap/scss/mixins';

//Adding New Color Start
$custom-theme-colors: (
  "altlight": #d63a3a,
  "altdark": #522192
);
$theme-colors: map-merge($custom-theme-colors, $theme-colors);
$theme-colors-rgb: map-loop($theme-colors, to-rgb, "$value");
$utilities-colors: map-merge(
  $theme-colors-rgb,
  (
    "black": to-rgb($black),
    "white": to-rgb($white),
    "body":  to-rgb($body-color)
  )
);
$utilities-text-colors: map-loop($utilities-colors, rgba-css-var, "$key", "text");
$utilities-bg-colors: map-loop($utilities-colors, rgba-css-var, "$key", "bg");
//Adding New Color End
```