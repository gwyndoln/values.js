# values.js
[![npm-image](https://img.shields.io/npm/v/values.js.svg)](https://www.npmjs.com/package/values.js)
![license-image](https://img.shields.io/npm/l/values.js.svg)
[![Known Vulnerabilities](https://snyk.io/test/npm/values.js/badge.svg)](https://snyk.io/test/npm/values.js)
[![Dependencies](https://img.shields.io/david/noeldelgado/values.js.svg)](https://david-dm.org/noeldelgado/values.js)
[![devDependencies](https://img.shields.io/david/dev/noeldelgado/values.js.svg)](https://david-dm.org/noeldelgado/values.js?type=dev)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/noeldelgado/values.js.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/noeldelgado/values.js/alerts/)
[![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/noeldelgado/values.js.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/noeldelgado/values.js/context:javascript)

Get tints and shades of a CSS color

> _The lightness or darkness of a color is called its value.
Tints are light values that are made by mixing a color with white, which increases lightness. Shades are dark values that are made by mixing a color with black, which reduces lightness._

## Demo
https://noeldelgado.github.io/values.js/

### Supports
* \<color value\>
	* Hexadecimal RGB value: #RGB #RRGGBB
	* #RGBA #RRGGBBAA (4 and 8-digit hexadecimal RGBA notation)
	* RGB/A - CSS Color Module Level 3 and 4 (number, percentage)
	* HSL/A - CSS Color Module Level 3 and 4 (number, deg, rad, turn)
* \<color keyword\>
	* One of the [pre-defined color keywords](https://www.w3.org/wiki/CSS/Properties/color/keywords).
* transparent
	* Shorthand for transparent black, rgba(0,0,0,0).

### Does not support
* currentColor
* inherit

## Installation

**NPM**

```sh
npm install values.js --save
```

Or as a `<script>` tag from a CDN as `Values`:

**Unpkg CDN**

```html
<script src="https://unpkg.com/values.js"></script>
```

**jsDelivr CDN**

```html
<script src="https://cdn.jsdelivr.net/npm/values.js"></script>
```

## Usage Example
```js
var Values = require('values.js')
  , color = new Values('#0099ff');

console.log(color.hex)              // => "0099ff"
console.log(color.rgb)              // => {r:0, g:153, b:255}
console.log(color.hsl) 	            // => {h:204, s: 100, l: 50}

console.log(color.hexString())      // => "#0099ff"
console.log(color.rgbString()) 	    // => "rgb(0, 153, 255)"
console.log(color.hslString())      // => "hsl(204, 100%, 50%)"

console.log(color.getBrightness())  // => 53

color.tints().forEach(function(tint) {
  console.log(tint);     // => [Values instance]
});

color.shades().forEach(function(shade) {
  console.log(shade);    // => [Values instance]
});

// tints, original color and shades
color.all().forEach(function(color) {
  console.log(color);   // => [Value instance]
});
```
## Instance
```js
// console.log(new Values('#09f'))
{
	hex: "09c"
	hsl: { h: 195, s: 100, l: 40 }
	rgb: { r: 0, g: 153, b: 204 }
	...
}
```

## Instance Methods

### setColor(String:color)
```js
/* Sets the base color for which all operations are based. Updates the instance's properties.
 * @param {string} color - A valid color format (#000, rgb(0,0,0), hsl(0,0%,0%))
 * @return {Values|Error}
 */

color.setColor('ff0');
color.setColor('rgb(255,255,0)');
color.setColor('hsl(60,100%,50%)');
```

### tint([Number:percentage=50])
```js
/* Lightens the instance by mixing it with white as specified by @percentage.
 * @param {number} [percentage=50]
 * @return {Values}
 */

color.tint();
color.tint(10);
color.tint(24);
```

### shade([Number:percentage=50)
```js
/* Darkens the instance color by mixing it with black as specified by @percentage.
 * @param {number} [percentage=50]
 * @return {Values}
 */

color.shade();
color.shade(9);
color.shade(31);
```

### tints([Number:percentage=10])
````js
/* Generates the tints of the instance color as specified by @percentage.
 * @param {number} [percentage=10]
 * @return {Array<Values>}
 */

color.tints(20).forEach(function (tint) {
    console.log(tint)
})
````

### shades([Number:percentage=10])
````js
/* Generates the shades of the instance color as specified by @percentage.
 * @param {number} [percentage=10]
 * @return {Array<Values>}
*/

color.shades(20).forEach(function (shade) {
    console.log(shade)
})
````

### all([Number:percentage=10])
```js
/* Generates the tints and shades of the instance color as specified by @percentage.
 * @param {number} [percentage=10]
 * @return {Array<Values>}
 */

color.all().forEach(function (color) {
    console.log(color)
})
```

### getBrightness()
````js
/* Calculates the brightness of the instance base-color.
 * @return {number} the base-color brightness.
 */
color.getBrightness();
````

### hexString()
```js
/* Returns the instance color in hexadecimal string form.
 * @returns {string} e.g. '#000000'
 */
 color.hexString();
```

### rgbString()
```js
/* Returns the instance color in rgb string form.
 * @returns {string} e.g. 'rgb(0, 0, 0)'
 */
color.rgbString();
```

## Dev
```sh
npm install 	# install dev-dependencies
npm test		# run the tests
npm run dev 	# watch for changes and run tests
```

## Related
- [Shadowlord](https://github.com/noeldelgado/shadowlord) - Tints and shades generator tool

## License
MIT © [Noel Delgado](http://pixelia.me/)
