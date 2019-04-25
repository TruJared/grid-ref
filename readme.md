# Css Grid Reference

Thanks [Css Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)

## template

### rows and columns

- Use to define your rows and columns
- Best practice to name columns
- Also if not using fixed width use `FR`s
- Don't forget `auto` will fill remaining space
- You can use repeat

#### samples

```css
display: grid;
grid-template-columns: 150px 250px auto 250px 150px;
grid-template-rows: 150px auto 150px;

// or //
display: grid;
grid-template-columns: 1fr 2fr 1fr 5fr;
grid-template-rows: 1fr 1fr 1fr 3fr;

// or named and with mixed units //
display: grid;
grid-template-columns: [column-left] 1fr [column-middle] 250px [column-right] 1fr [column-end];
grid-template-rows: [row-top] 1fr [row-middle] auto [row-bottom] 2fr [row-end];

// here's some repeat //
display: grid;
grid-template-columns: repeat(2, 150px) auto repeat(2, 150px);
grid-template-rows: 1fr 2fr 1fr;
```

### area

- useful for defining very specific layouts
- the use of names helps make things very explicit
- every grid section must have a name or use `.` for empty

#### sample

this will "mess up" the order of the boxes 💥
