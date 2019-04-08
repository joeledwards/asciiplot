# asciiplot

Console ASCII line charts in pure Javascript (for NodeJS) with no dependencies. This code is absolutely free for any usage, you just do whatever the fuck you want.

<img width="789" alt="Console ASCII Line charts in pure Javascript (for NodeJS)" src="https://cloud.githubusercontent.com/assets/1294454/22818709/9f14e1c2-ef7f-11e6-978f-34b5b595fb63.png">

## Usage

### NodeJS

```sh
npm install asciiplot
```

```javascript
var asciiplot = require ('asciiplot')
var s0 = new Array (120)
for (var i = 0; i < s0.length; i++)
    s0[i] = 15 * Math.sin (i * ((Math.PI * 4) / s0.length))
console.log (asciiplot.plot (s0))
```

### Options

The width of the chart will always equal the length of data series. The height and range are determined automatically.

```javascript
var s0 = new Array (120)
for (var i = 0; i < s0.length; i++)
    s0[i] = 15 * Math.sin (i * ((Math.PI * 4) / s0.length))
console.log (asciiplot.plot (s0))
```

<img width="788" alt="Console ASCII Line charts in pure Javascript (for NodeJS)" src="https://cloud.githubusercontent.com/assets/1294454/22818807/313cd636-ef80-11e6-9d1a-7a90abdb38c8.png">

The output can be configured by passing a second parameter to the `plot (series, config)` function. The following options are supported:
```javascript
var config = {

    offset:  3,          // axis offset from the left (min 2)
    padding: '       ',  // padding string for label formatting (can be overrided)
    height:  10,         // any height you want

    // the label format function applies default padding
    format:  function (x, i) { return (padding + x.toFixed (2)).slice (-padding.length) }
}
```

### Scale To Desired Height

<img width="791" alt="Console ASCII Line charts in pure Javascript (for NodeJS)" src="https://cloud.githubusercontent.com/assets/1294454/22818711/9f166128-ef7f-11e6-9748-b23b151974ed.png">

```javascript
var s = []
for (var i = 0; i < 120; i++)
    s[i] = 15 * Math.cos (i * ((Math.PI * 8) / 120)) // values range from -15 to +15
console.log (asciiplot.plot (s, { height: 6 }))     // this rescales the graph to ±3 lines
```

<img width="787" alt="Console ASCII Line charts in pure Javascript (for NodeJS)" src="https://cloud.githubusercontent.com/assets/1294454/22825525/dd295294-ef9e-11e6-93d1-0beb80b93133.png">


### Auto-range

```javascript
var s2 = new Array (120)
s2[0] = Math.round (Math.random () * 15)
for (i = 1; i < s2.length; i++)
    s2[i] = s2[i - 1] + Math.round (Math.random () * (Math.random () > 0.5 ? 2 : -2))
console.log (asciiplot.plot (s2))
```

<img width="788" alt="Console ASCII Line charts in pure Javascript (for NodeJS)" src="https://cloud.githubusercontent.com/assets/1294454/22818710/9f157a74-ef7f-11e6-893a-f7494b5abef1.png">

