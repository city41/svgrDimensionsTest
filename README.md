# SVGR dimensions issue

If the svg file is in `/tmp`, then `dimensions` in the config file is ignored

## repro

### working case

run `yarn svgr sample.svg`

The output is as expected: typescript and no `width` or `height` on `<svg>`.

### non-working case

```sh
cp sample.svg /tmp/sample.svg
yarn svgr /tmp/sample.svg
```

The output is not expected: it is in typescript, but `width` and `height` are present on `<svg>`.

Since the output is typescript and not javascript, it seems like svgr is reading `typescript: true` from the config but not `dimensions: false` from the config.


