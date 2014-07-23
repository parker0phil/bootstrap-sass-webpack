bootstrap-webpack
=================

Bootstrap configuration and loading package for webpack, using `bootstrap-sass`.

Credit for the original goes to Scott Bleck (@bline).


Usage
-----

Bootstrap use some fonts. You need to configure the correct loaders in your `webpack.config.js`. Example:

``` javascript
module.exports = {
  module: {
    loaders: [
      // the url-loader uses DataUrls.
      // the file-loader emits files.
      { test: /\.woff$/,   loader: "url-loader?limit=10000&minetype=application/font-woff" },
      { test: /\.ttf$/,    loader: "file-loader" },
      { test: /\.eot$/,    loader: "file-loader" },
      { test: /\.svg$/,    loader: "file-loader" }
    ]
  }
};
```

### Complete Bootstrap

To use the complete bootstrap package including styles and scripts with the default settings:

``` javascript
require("bootstrap-sass-webpack");
```

### Custom configuration

You can configurate bootstrap-sass-webpack with two configuration files:

* `bootstrap-sass.config.js`
* `bootstrap-sass.config.less`

Add both files next to each other to your project. And:

``` javascript
require("bootstrap-sass-webpack!./bootstrap-sass.config.js");
```

Or simple add it as entry point to your `webpack.config.js`:

``` javascript
module.exports = {
  entry: [
    "bootstrap-sass-webpack!./bootstrap-sass.config.js",
    "your-existing-entry-point"
  ]
};
```

#### `bootstrap-sass.config.js`

Example:

``` javascript
module.exports = {
  scripts: {
    // add every bootstrap script you need
    'transition': true
  },
  styles: {
    // add every bootstrap style you need
    "mixins": true,

    "normalize": true,
    "print": true,

    "scaffolding": true,
    "type": true,
  }
};
```

#### `bootstrap-sass.config.less`

Write less code. I. e. overwrite the default colors or sizes.

Example:

``` less
@font-size-base:          24px;

@btn-default-color:              #444;
@btn-default-bg:                 #eee;
```