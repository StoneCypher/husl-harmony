# husl_harmony
Use the HUSL library to generate more effective and better balanced color harmonies.

## Example

By example, asking `husl_harmony` for the first 14 swatch sets for color `#3D7AFA` yields these:

![](https://raw.githubusercontent.com/StoneCypher/husl-harmony/master/src/html/palettes.png).

That palette set is generated by [this code](https://github.com/StoneCypher/husl_harmony/blob/master/src/html/index.html#L10):

`husl_harmony` is mostly meant for code use, and primarily ships back arrays of hex-6 colors of the form `['#aabbcc', '#ddeeff']`.
Its results are best when used with tertiary, mid-saturation colors (colors where none of the three RGB color channels are 
near-max or near-zero.)

`husl_harmony` also includes a [harmonious gray balancer with color overlay 
calculation](https://www.smashingmagazine.com/2016/04/web-developer-guide-color/#creating-harmonious-grays), which is great 
for making color-hinted websites.

```javascript
window.onload = function() { 

    var husl_harmony = require('husl_harmony'),
        swatch_div   = husl_harmony.make_all_swatches('#3D7AFA');

    document.body.innerHTML = '<h1>All swatch sets matching <tt>#3D7AFA</tt></h1>';
    document.body.appendChild(swatch_div); 

}
```

Color swatch sets will be balanced in hue, saturation, lightness, and oriented to the source color.

## ES6 Usage

```javascript
// let's get the analogous-7 matches of our color, a dark blue, #0026ff
import {from_rgb} from './husl_harmony.js';
console.log( from_rgb('#0026FF', 'analogous-7') );
```

The result should be 
```
["#005e53", "#005c64", "#00597b", "#0026FF", "#8e00a9", "#9c007e", "#a50051"]
```

## ES5 Usage

```javascript
// see dist/index.html for a working example
var hh = require('husl_harmony');
console.log( hh.from_rgb('#0026FF', 'analogous-7') );
```

The result should be 
```javascript
["#005e53", "#005c64", "#00597b", "#0026FF", "#8e00a9", "#9c007e", "#a50051"]
```

## Harmonies

Currently, the library supports sixteen harmonies:

1. Monochromatic 
1. Complementary
1. Split complementary
1. Double complementary
1. L-double complementary
1. Triad
1. Complementary triad
1. Square
1. Tetrad
1. L-tetrad
1. Pentagon
1. Hexagon
1. Analogous 3
1. Analogous 5
1. Analogous 7
1. Complementary analogous

[It's easy and encouraged to add more](https://github.com/StoneCypher/husl_harmony/blob/master/src/js/husl_harmony.js#L14)! :smile: