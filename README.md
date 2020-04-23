# dnd combat tracker

## things to consider

- track character information
  - name
  - hp
  - ac
  - initiative
  - passive perception
  - statuses
    - add custom bonuses or ailments (restrained, bless etc)
    - duration
- track monster information
  - name
  - hp
  - ac
  - initiative
  - passive perception
  - statuses
    - add custom bonuses or ailments (prone, bless etc)
    - duration
  - get monster information from API
    - _FUTURE ENHANCEMENT_
- values are not required and can be overridden manually
- the ability to add/remove multiple characters/monsters
  - _maybe_ the ability to roll initiative for all monsters
  - _stick with manual rolling for now_
- automatically increment turn counter at the end of character turn
- automatically increment rounc counter at the end of each character turn
- decrement turn/round counter on _back_
- time conversion section
  - mins to hours, seconds, rounds, turns etc

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
