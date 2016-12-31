# Plumber box
[Plumber](https://jamonserrano.github.io/plumber-sass) extension to align boxes to the vertical grid.

Use this mixin whenever you need to add margins, paddings, and borders to a flexible container element without breaking the grid.

## Installation

First, make sure to [install and import plumber-sass](https://jamonserrano.github.io/plumber-sass/#toc_1) before using plumber-box.

### Manual
Download and extract [the latest release](https://api.github.com/repos/jamonserrano/plumber-box/zipball), move `_plumber-box.scss` into the vendor folder of your project and import it:

```scss
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

1\. Set up the grid height for Plumber if you haven't done it before:

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

This will generate the following CSS:

```css
blockquote {
	margin-top: 2rem;
	padding-top: 1rem;
	margin-bottom: 0;
	padding-bottom: 1rem;
}
```

### Borders
Borders can be set on the inside or on the outside of the box, taking away some space from the padding or margin respectively.

#### Inside
Add the `$border` parameter to the mixin, define borders and box-sizing:

```scss
blockquote {
	@include plumber-box(
		$margin: 2 0,
		$border: 2px 2px,
		$padding: 1 1
	);

	border: 2px solid gold;
	box-sizing: border-box;
}
```

> The border width will be substracted from the padding.

#### Outside
Use the CSS `outline` property to add outside borders:

```scss
blockquote {
	@include plumber-box(
		$margin: 2 0,
		$padding: 1 1
	);

	outline: 2px solid gold;
}
```

> The outline will visually decrease the margin but it is not included in the element size so it won't break the grid.
>
> Rounded borders are not possible with this method.


### Shorthands
You can use shorthands to set the same top and bottom values:

```scss
blockquote {
	@include plumber-box(
		$margin: 2, // top and bottom margin
		$border: 1px // top and bottom border
		$padding: 1 // top and bottom padding
	);
}
```


## API

### plumber-box
The main mixin.

**Parameters:** All parameters are optional, the default grid height can be set with `plumber-set-defaults`.


Name | Description | Type | Default value
---- | ----------- | ---- | -------------
$grid-height | Override the default grid height | Any unit | As set in Plumber
$margin | Top and bottom margin as a multiple of grid height | One or two integers | `0`
$border | Top and bottom border width | One or two non-negative `px` values or `0`s | `0px`
$padding | Top and bottom padding as a multiple of grid height | One or two non-negative integers | `0`

**Output:** `margin-top`, `margin-bottom`, `padding-top`, `padding-bottom` properties with the same unit as the grid height.

## License

MIT License
