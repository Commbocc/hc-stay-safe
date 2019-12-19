# Stay Safe Components

## Locations

List locations in [this spreadsheet](https://docs.google.com/spreadsheets/d/14c7p2JUfuRTC9JcbvG--pOu6IRtVuMZ7Flkv0EZ54Io/edit#gid=1066978540) in a table. The `table-index` property defines which sheet of the spreadsheet to use. Rows will automatically be removed as the End Date/Time passes.

```html
<!-- Sandbag Locations -->
<div is="Locations" title="Sandbag Locations" table-index="1">&nbsp;</div>
<!-- Evacuation Shelters -->
<div is="Locations" title="Evacuation Shelters" table-index="2">&nbsp;</div>
<!-- Cold Weather Shelters -->
<div is="Locations" title="Cold Weather Shelters" table-index="3">&nbsp;</div>
```

## Links

```html
<div is="Links" title="Report Damage">
  <a href="#">Downed Trees or Other Debris</a>
  <a href="#">Flooding or Drainage Issues</a>
</div>
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
