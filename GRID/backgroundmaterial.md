# TO CREATE A GRID:

<span style="background-color:yellow">container - **display: grid**</span>
set column and row sizes with <span style="background-color:yellow">**grid-template-columns** and **grid-template-rows**</span>

<span style="background-color:yellow">on children - apply **grid-column** and **grid-row**</span>
<br/><br/>
# TERMINOLOGY:

- *grid container*: the direct parent of all the grid items
- *grid line*: the dividing lines that make up the structure of the grid, they can be vertical or horizontal
- *grid track*: the space between 2 adjacent grid lines
- *grid area*: total space surrounded by 4 grid lines
- *grid item*: children of the grid container
- *grid cell*: 1 cell
<br/><br/>
# GRID PROPERTIES:

## <span style= "color: purple">1. Grid container properties</span>

<span style= "background-color: lightgreen">**`display: grid`**</span> - block level grid

**`display: inline-grid`** -  inline level grid

<span style= "background-color: lightgreen">**`grid-template-columns`**</span> and <span style= "background-color: lightgreen">**`grid-template-rows`**</span> - defines the columns and rows of the grid, values are track size and line names (space by default)

Grid lines are automatically assigned numbers from these assignments (first line is *1*, last line is *-1*, numbered from both directions)

You can NAME THE LINES (you can give more than 1 name to a line) with a BRACKET SYNTAX:

**`grid-template-columns: [first] 40px [col1-end col2-start] 50px [line3] auto [col4-start] 50px [five] 40px [end];`**

you can use the *repeat()* notation:
**`grid-template-rows: repeat(3, 20px [col-start]);`**

if multiple lines share the same name, they can be referenced by their line name and count:
<span style= "background-color: lightgreen">**`grid-column-start: col-start 2;`**</span>

*fr* unit represents a fraction of the free space of the grid container, you can set track sizes with it.
The free space is calculated AFTER non-flexible items, so for example here the total amount of free space available to the fr units doesn't include the 50px:
**`grid-template-columns: 1fr 50px 1fr 1fr;`**

<span style= "background-color: lightgreen">**`grid-template-areas`**</span> defines a grid template by referencing the names of the grid areas which are specified with the grid-area property (the name you give them). Repeating the name of a grid area causes the content to span those cells. A PERIOD signifies an empty cell. **`grid-template-areas`** provides a visualization of the structure of the grid. Values are: *grid-area-name*, . (period aka empty grid cell), *none* (no grid areas defined).:

```c
.container {
  grid-template-areas:
    "<grid-area-name> | . | none | ..."
    "...";
}
```
grid-area-name is specified with <span style= "background-color: lightgreen">**`grid-area`**</span>(on the children):

```c
.item-a {
  grid-area: header;
}
.item-b {
  grid-area: main;
}
.item-c
  grid-area: sidebar;
}
.item-d {
  grid-area: footer;
}

.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas:
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer"
}
```
Each row in the **`grid-template-areas`** declaration needs to have the same number of cells, so if there are empty cells use period to indicate that (don't just leave it empty). You can use multiple adjacent periods to declare a single empty cell.

When you use **`grid-template-areas`**, the start and end lines of the areas are getting named automatically.

<span style= "background-color: lightgreen">**`grid-template`**</span> is the shorthand for setting **`grid-template-rows, grid-template-columns`** and **`grid-template-areas`**:

```c
.container {
  grid-template: none | <grid-template-rows> / <grid-template-columns>
}
```

```c
.container {
  grid-template:
    [row1-start] "header header header" 25px [row1-end]
    [row2-start] "footer footer footer" 25px [row2-end]
    / auto 50px auto;
}
```
<span style= "background-color: lightgreen">**`column-gap`**</span> and <span style= "background-color: lightgreen">**`row-gap`**</span> specifiy the size of the grid lines (width of the gutters between columns / rows).
Gaps (gutters) are only created between the columns and rows, not on the outer edges.

<span style= "background-color: lightgreen">**`gap`**</span> is the shorthand for **`column-gap`** and **`row-gap`**:

```c
.container {
  gap: <grid-row-gap> <grid-column-gap>;
}
```
If no row-gap is specified, it is set to the same value as column-gap.

<span style= "background-color: lightgreen">**`justify-items`**</span> aligns grid items along the inline axis (row). Applies to all grid items inside the container.

**`justify-items: start | end | center | stretch`** 

Default is stretch (fill the whole width of the cell).

<span style= "background-color: lightgreen">**`justify-self`**</span> does the same on individual grid items.

<span style= "background-color: lightgreen">**`align-items`**</span> aligns grid items along the block axis (column). Applies to all grid items inside the container.

**`align-items: start | end | center | stretch | baseline`**

Default is stretch (fill the whole height of the cell)
baseline means align items along TEXT BASELINE.

<span style= "background-color: lightgreen">**`align-self`**</span> same thing for individual grid items

Modifiers for align-items: SAFE and UNSAFE - safe keyword means only until item doesnt overflow otherwise change alignment (to start, so horizontal scroll doesnt appear) unsafe will allow moving content into inaccessible areas ("data loss").
Safe alignment leads the browser to always place elements accessible to the user (visible on the viewport).

<span style= "background-color: lightgreen">**`place-items`**</span> is a shorthand for align-items and justify-items:

```c
.center {
  display: grid;
  place-items: center;
}
```
**`place-items: align-items justify-items`**

If the second value is omitted, first value will be set for justify-items too

If your grid is smaller than the grid container:
<span style= "background-color: lightgreen">**`justify-content`**</span>
Aligns the ENTIRE GRID along the inline row axis

<span style= "background-color: lightgreen">**`align-content`**</span>
Aligns the ENTIRE GRID along the block axis

**`justify-content: start | end | center | stretch | space-around | space-between | space-evenly`**

stretch resizes the grid items to allow the grid to fill the full width of the grid container (evenly i guess)

**`align-content: start | end | center | stretch | space-around | space-between | space-evenly`**

<span style= "background-color: lightgreen">**`place-content`**</span> is a shorthand for align-content and justify-content (align-content / justify-content), if the second value is omitted, the first value is assigned to both properties

<span style= "background-color: lightgreen">`grid-auto-columns`**</span>** and <span style= "background-color: lightgreen">**`grid-auto-rows`**</span> specify the size of any auto-generated grid tracks (implicit grid tracks). Implicit grid tracks get created when there are more grid items than cells in the grid or when a grid item is placed outside of the grid.

```c
.container {
  grid-template-columns: 60px 60px;
  grid-template-rows: 90px 90px;
  grid-auto-columns: 60px;
}
```

<span style= "background-color: lightgreen">**`grid-auto-flow`**</span> controls how the auto placement algorith works (grid items are automatically placed on the grid, you can control the direction of the auto placement with this)

```
.container {
  grid-auto-flow: row | column | row dense | column dense;
}
```
dense attempts to fill in earlier holes in the grid if smaller items come up later, might cause items to appear out of order

<span style= "background-color: lightgreen">**`grid`**</span> is a shorthand for: **`grid-template-rows, grid-template-columns, grid-template-areas, grid-auto-rows, grid-auto-columns`**, and **`grid-auto-flow `**

```c
.container {
  grid: 100px 300px / 3fr 1fr;
}

.container {
  grid-template-rows: 100px 300px;
  grid-template-columns: 3fr 1fr;
}
```

```
.container {
  grid: [row1-start] "header header header" 1fr [row1-end]
        [row2-start] "footer footer footer" 25px [row2-end]
        / auto 50px auto;
}

EQUALS

.container {
  grid-template-areas: 
    "header header header"
    "footer footer footer";
  grid-template-rows: [row1-start] 1fr [row1-end row2-start] 25px [row2-end];
  grid-template-columns: auto 50px auto;
}
```
<div style= "background-color: white">

### <span style= "color: hotpink; background-color: white">**ALL GRID CONTAINER PROPERTIES:**</span>

- ### <span style= "color: blue; letter-spacing: 1.5px">display: grid

- ### <span style= "color: blue; letter-spacing: 1.5px">grid-template-columns<span style= "color: blue; letter-spacing: 1.5px">
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-template-rows
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-column &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-column-start &nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-column-end &nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-row &nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-row-start &nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-row-end &nbsp;</span> *children
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-template-areas
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-area
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-template
- ### <span style= "color: blue; letter-spacing: 1.5px">column-gap
- ### <span style= "color: blue; letter-spacing: 1.5px">row-gap
- ### <span style= "color: blue; letter-spacing: 1.5px">gap
- ### <span style= "color: blue; letter-spacing: 1.5px">justify-items
- ### <span style= "color: blue; letter-spacing: 1.5px">justify-self
- ### <span style= "color: blue; letter-spacing: 1.5px">align-items
- ### <span style= "color: blue; letter-spacing: 1.5px">align-self
- ### <span style= "color: blue; letter-spacing: 1.5px">place-items
- ### <span style= "color: blue; letter-spacing: 1.5px">justify-content
- ### <span style= "color: blue; letter-spacing: 1.5px">align-content
- ### <span style= "color: blue; letter-spacing: 1.5px">place-content
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-auto-columns
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-auto-rows
- ### <span style= "color: blue; letter-spacing: 1.5px">grid-auto-flow
- ### <span style= "color: blue; letter-spacing: 1.5px">grid
</div>