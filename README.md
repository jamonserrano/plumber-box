# Plumber box
[Plumber](https://jamonserrano.github.io/plumber-sass) extension to align boxes to the vertical grid.

Use this mixin whenever you need to add margins and paddings to a container element without breaking the grid.

## Installation

First, make sure to [install and import plumber-sass](https://jamonserrano.github.io/plumber-sass/#toc_1) before using plumber-box.

### Manual
Download and extract [the latest release](https://api.github.com/repos/jamonserrano/plumber-box/zipball), move `_plumber-box.scss` into the vendor folder of your project and import it:

```sass
@import "vendor/plumber-box";
```

### NPM / Yarn
Install:

```sh
# NPM
$ npm install plumber-box --save-dev

# Yarn
$ yarn add plumber-box --dev
```
And import it in your project:

```scss
@import "node_modules/plumber-box/plumber-box";
```

### Bower
Install:

```sh
$ bower install plumber-box --save-dev
```
And import it in your project:

```scss
@import "bower_components/plumber-box/plumber-box";
```

## Usage

1\. Set up the grid height for Plumber:

```scss
@include plumber-set-defaults($grid-height: 1rem);
```

2\. Include the plumber-box mixin. Specify margins and paddings as multiples of the grid height. 

```scss
blockquote {
	@include plumber-box(
		$margin: 2 0, // top margin: 2, bottom margin: 0
		$padding: 1 1 // top padding: 1, bottom padding: 1
	);
}
```

### Shorthand values
You can use shorthand values to set the same top and bottom values:

```scss
blockquote {
	@include plumber-box(
		$margin: 2, // top and bottom margin
		$padding: 1 // top and bottom padding
	);
}
```

### Borders
Use outlines instead of borders when styling plumber boxes – outlines are not included in the element size so they won't break the grid.
```scss
blockquote {
	// bad
	// border: 1px solid gold;
	
	// good
	outline: 1px solid gold;
}
```


## API

### plumber-box
The main mixin.

**Parameters:** All parameters are optional, the default grid height can be set with `plumber-set-defaults`.


Name | Description | Type | Default value
---- | ----------- | ---- | -------------
$grid-height | Grid height | Any unit | 1rem
$margin | Top and bottom margin as a multiple of grid height | One or two integers | 0
$padding | Top and bottom padding as a multiple of grid height | One or two non-negative integers | 0

**Output:** `margin-top`, `margin-bottom`, `padding-top`, `padding-bottom` properties with the same unit as the grid height.

## License

MIT License
