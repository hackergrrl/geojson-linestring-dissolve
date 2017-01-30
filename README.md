# geojson-linestring-dissolve

> Dissolve connected GeoJSON LineStrings into a single LineString.

## Usage

```js
var dissolve = require('geojson-linestring-dissolve')

var line1 = {
  type: 'LineString',
  coordinates: [
    [0.0, 0.0],
    [1.0, 1.0],
    [2.0, 2.0]
  ]
}

var line2 = {
  type: 'LineString',
  coordinates: [
    [2.0, 2.0],
    [3.0, 3.0]
  ]
}

console.log(dissolve([line1, line2]))
```

outputs

```
{
  type: 'LineString',
  coordinates: [
    [0.0, 0.0],
    [1.0, 1.0],
    [2.0, 2.0],
    [3.0, 3.0]
  ]
}
```

## API

```js
var dissolve = require('geojson-linestring-dissolve')
```

### dissolve([lineStrings])

Consumes an array of [GeoJSON](http://geojson.org/geojson-spec.html)
`LineString`s, and returns a new GeoJSON `LineString` object, with all touching
`LineString`s dissolved into a single unit. If the `LineString`s are
non-contiguous, a `MultiLineString` is returned.

## Install

With [npm](https://npmjs.org/) installed, run

```
$ npm install geojson-linestring-dissolve
```

## Caveats

There are some cases that this module does not *yet* handle:

1. `LineString`s that fork or junction are returned as two separate
   `LineString`s -- one fork is chosen at random.
2. Forks or junctions are only detected if they occur at the `LineString`'s head
   or tail coordinate.

See a use case that you know how to fill in? PRs welcome!

## License

ISC

