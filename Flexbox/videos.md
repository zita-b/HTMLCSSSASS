**display: flex**

.box*5>{$$$$$} will create:
<div class="box">00001</div>
.
.
.
<div class="box">00005</div>

content inside curly braces, $$$$$ for 5 digits ending with order number of divs

apply **display: flex** to container -->
line breaks and spaces in html will be ignored, spaces between elements disappear
height by default will equal height of container, you can set height with height property
flex children have INLINE BLOCK behaviour basically
can apply padding with padding
In conclusion, any display rule (inline, inline-block etc) for flex children is useless

You can apply margin to flex children
margin collapse doesn't happen between flex children (just like inline block elements)!
margins of 2 adjacent elements overlap by default with block elements
you can set **flex-direction: column** so elements will be displayed below one another instead of default next to each other like in a row
if flex container only has one child --> it will be located in the top left corner of the container
inside flex container margin: auto works both horizontally and vertically, so you can center elements inside flex container by setting **margin: auto**
(if there are more than 1 elements the space between them will be divided equally if you set margin: auto)

Order of elements inside flex container --> 
default is that flex children are located on the same line from left to right, in the same order as they come in the HTML, this is **flex-direction: row** which again is the default
If you set flex-direction: column, flex children will be below one another
you also reverse their order by **flex-direction: column-reverse, row-reverse**
elements have order value, default is 0
in flex container elements line up from lowest order to highest, so if you set -1 to an element it will come first
so order value provides priority value and inside flex container lowest order value will come first

flex-direction sets the MAIN AXIS direction for the container (row or column)
If you set flex-direction to reverse elements will be displayed from the right(row-reverse) or bottom(column-reverse)
if flex children don't fit inside the container they overflow and a scroll will appear --> to override this use **flex-wrap: wrap**
if you set flex-wrap: wrap, all elements that can not fit in the first line will be displayed on a new line but the container height wont change (elements will shrink instead)
**flex-wrap:wrap-reverse** to start displaying from bottom new line or from the right
--> so in conclusion, if the flex container has more elements than it can fit, the flex children will overflow and a scroll might appear, you can control this behaviour with flex-wrap: wrap, wrap-reverse

**justify-content** --> used to align flex children on the main axis
default value is flex-start(elements will start on the beginning of main axis aka flex-direction so left or top if not reversed)
**justify-content: flex-end**  --> flex children aligned to the end of the main axis of the flex-container (so like reverse-row or reverse-column if its not set except order of elements wont change)
**justify-content: flex-start, flex-end, center, space-between, space-evenly,space-around**

**align-items** --> cross axis alignment for all flex children
default value is stretch (elements take up all available width or height in their line)
**align-items: flex-start** --> will render elements' original size
flex-end --> same but will start on other end of cross axis
**align-items: flex-start, flex-end, center, baseline**
baseline puts them on the bottom of the first line of each elements
As opposed to align-items which we apply to the flex container, we can control the alignment of individual elements with **align-self**
align-self has same values as align-items and align-self overrides align-items

in MULTILINE flex containers (when there are too many flex children to fit so we use flex wrap: wrap) **justify-content** works separately for each line (depending on the available space)
**align-content** controls FULL ROW (alignment and stretch)
**align-content: stretch** rows occupy full height of container
by default the height of the rows will be the height of the biggest element

center an element inside it's container (one element):

```json
.container {
  display: flex;
  justify-content: center:
  align-items: center
}
```

center text inside an element:

```json
{
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
```
--> this will work even if you change the text

