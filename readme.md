# Css Grid Reference

Thanks [Css Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)

## template

### rows and columns

- Use to define your rows and columns
- Also if not using fixed width use `FR`s
- Don't forget `auto` will fill remaining space
- You can use repeat

```css
.container {
  display: grid;
  grid-template-columns: 150px 250px auto 250px 150px;
  grid-template-rows: 150px auto 150px;
}
// or //
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr 5fr;
  grid-template-rows: 1fr 1fr 1fr 3fr;
}
// or named and with mixed units //
.container {
  display: grid;
  grid-template-columns: [column-left] 1fr [column-middle] 250px [column-right] 1fr [column-end];
  grid-template-rows: [row-top] 1fr [row-middle] auto [row-bottom] 2fr [row-end];
}
// here's some repeat //
.container {
  display: grid;
  grid-template-columns: repeat(2, 150px) auto repeat(2, 150px);
  grid-template-rows: 1fr 2fr 1fr;
}
```

### area

- useful for defining very specific layouts
- the use of names helps make things very explicit
- every grid section must have a name or use `.` for empty

this will "mess up" the order of the boxes 💥

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: auto;
  grid-template-areas:
    'one two three'
    'four five six'
    'seven eight nine'
    'ten eleven twelve';
}
... .box--1 {
  background: teal;
  grid-area: five;
}
.box--2 {
  background: yellow;
  grid-area: seven;
}
...

// or a grid layout //
.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas:
    'header header header header'
    'main main . sidebar'
    'footer footer footer footer';
}
```

### shortcuts 👍

`grid-template`

```css
.container {
  grid-template:
    [row1-start] 'header header header' 25px [row1-end]
    [row2-start] 'footer footer footer' 25px [row2-end]
    / auto 50px auto;
}
```

is the same as

```css
.container {
  grid-template-rows: [row1-start] 25px [row1-end row2-start] 25px [row2-end];
  grid-template-columns: auto 50px auto;
  grid-template-areas:
    'header header header'
    'footer footer footer';
}
```

❗️ if not interested in column/row names just use area names like:

```css
.container {
  grid-template:
    'header header header' 25px
    'footer footer footer' 25px
    / auto 50px auto;
}
```

## grid column gap and grid column row gap

- adds gaps 🚈
- think of it like gutters
- modern browsers are removing "grid" prefix

```css
.container {
  column-gap: <line-size>;
  row-gap: <line-size>;
}

// or simply //
.container {
  gap: <line-size> <line-size>;
}
```

## justify and align

pretty much the same as flexbox

### items

- align aligns items along the column
- `align-items: start | end | center | stretch;`
- justify aligns items along the row
- `justify-items: start | end | center | stretch;`
- `place-items` does both
- `place-items: <align-items> / <justify-items>`

### content

- this aligns the grid content itself
- useful when using fixed item sizes
- align aligns content along the columns
- `align-content: start | end | center | stretch | space-around | space-between | space-evenly;`
- justify aligns content along the row
- `justify-content: start | end | center | stretch | space-around | space-between | space-evenly;`
- `place-content` does both
- `place-content: <align-content> / <justify-content>`

## auto

- specifies the size of any auto-generated grid tracks

```css
grid-auto-columns: <track-size> ...;
grid-auto-rows: <track-size> ...;
```

- `grid-auto-flow` controls how the auto-placement algorithm works

```css
grid-auto-flow: row | column | row dense | column dense;
```

- **row**: tells the auto-placement algorithm to fill in each row in turn, adding new rows as necessary (default)
- **column**: tells the auto-placement algorithm to fill in each column in turn, adding new columns as necessary
- **dense**: tells the auto-placement algorithm to attempt to fill in holes earlier in the grid if smaller items come up later

## for the children

- `grid-column` specifies the size of a grid item across multiple columns
- `grid-column: <start-line> / <end-line> | <start-line> / span <value>;`
- `grid-row` specifies the size of a grid item across multiple rows
- `grid-row: <start-line> / <end-line> | <start-line> / span <value>;`
- `grid-area` gives an item a name so that it can be referenced by a template or super shorthand
- `grid-area: <name> | <row-start> / <column-start> / <row-end> / <column-end>;`

```css
.box--3 {
  grid-row: third-line / 4;
  grid-column: 3 / span 2;
}

// or
.box--3 {
  grid-area: 3 / 4 / 3 / span 2;
}

// or
.box--3 {
  grid-area: header;
}
```

### align and justify

- works the same as the "globals" but is applied to a single item
- `align-self: start | end | center | stretch;`
- `justify-self: start | end | center | stretch;`
- `place-self: <align-self> / <justify-self> ;`
