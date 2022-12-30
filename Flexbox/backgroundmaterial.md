Flexible box Module is a one-dimensional layout model

Flexbox deals with layout in one dimension at a time - row or column
Grid Layout is TWO DIMENSIONAL because it can control columns and rows together

Flexbox has two axes - main axis and cross axis
Main axis is flex direction

**flex-direction: row, row-reverse, column, column-reverse**

row and row reverse run in the INLINE DIRECTION

column and column-reverse run in the BLOCK DIRECTION

an area of a document laid out using flexbox is called a FLEX CONTAINER
to create a flex container, we set the container's display property to flex or inline flex
As soon as we do this the DIRECT CHILDREN of that container become FLEX ITEMS

Initial values for flex items:
flex-direction: row
items start from the start edge of main axis
items do not stretch on the main dimension, but can shrink
items will stretch to fill the size of cross axis
flex-basis is set to auto
flex-wrap is set to nowrap

flex-direction property of flex container allows us to change direction in which our flex items display
flex-direction: row-reverse will keep the items displaying along the row, however the START and END lines are SWITCHED

if we set flex-direction column the main axis switches and our items now display in a column
set column-reverse to switch start and end lines

Flexbox is one dimensional, but it is possible to cause our flex items to wrap onto multiple lines.
If you do that, consider each line as a new flex container.
to cause wrapping behaviour add the property flex-wrap with a value of wrap. Now, if your items are too large to all display in one line, they will wrap onto another line. You can set a width to your flex items, so either there are too many to fit with their default width or you set a width and they are too big.
flex-wrap initial value is nowrap. If flex-wrap is set to nowrap, the flex items will shrink to fit the container because they are using initial flexbox values that allows items to shrink. Nowrap causes an overflow if the items are not able to shrink because of a setting or could not shrink small enough to fit.

**flex-flow** shorthand is the combination of flex-direction and flex-wrap. The first value specified is flex-direction and the second value is flex-wrap.

We can target flex-items DIRECTLY, we have three properties for this:
**flex-grow**
**flex-shrink**
**flex-basis**

with these properties we can control the ratios of flex items on the main axis

These properties change the way the AVAILABLE SPACE is distributed amongst our items
If we have leftover space in our container (the width of the container is larger than the width of the items) according to initial values flexbox will put that space after the last item.

If we want the items to grow and fill the space, we need to apply the flex properties to individual items.

**flex-basis** defines the size of an item in terms of the space it leaves as available space.
The initial value of flex-basis is auto. Flex-basis auto means the browser looks to see if the item has a size. If they have a size that will be used as the flex-basis.

If the items don't have a set size then the CONTENT'S SIZE is used as flex-basis.
So initially if we just declare display: flex on the parent to create the flex items, the items all move into a row and take only as much space as they need to display their contents.

With the **flex-grow** property set to a positive integer, flex items can grow along the main axis from their flex-basis. This will cause the items to stretch and take up any available space on the main axis (or a proportion if multiple items are allowed to grow).
flex-grow property can be used to distribute space in proportion. 

**flex-shrink** property controls how space is taken away. If we do not have enough space in the container and flex-shrink is set to a positive integer, then the items can become smaller than the flex-basis. An item with a higher value set for flex-shrink will shrink faster than its siblings that have lower values.

flex-grow, flex-shrink and flex-basis properties are combined into the **flex** shorthand.
The flex shorthand allows you to set the three values in this order: flex-grow, flex-shrink, flex-basis

Predefined shorthand values for flex cover most of the use cases:
**flex: initial, auto, none, <positive number>**

flex: initial resets the item to the initial values of flexbox, it is the same as flex: 0 1 auto
flex: auto is the same as flex: 1 1 auto, same as initial except items can grow too
flex:none wil create fully inflexible flex items. Same as flex: 0 0 auto. Items cannot grow or shrink but will be laid out using flexbox with a flex-basis of auto.
flex: 1, flex: 2 etc mean flex: 1 1 0 flex: 2 1 0 and so on, items can grow and shrink from a flex-basis of 0

A key feature of flexbox is the ability to align and justify items on the main and cross axes, and to distribute space between flex items. These properties are to be SET on the FLEX CONTAINER:

**align-items** property will align the items on the CROSS AXIS
initial value of align-items is stretch, this is why flex items stretch to the height of the flex container by default.
If you set align-items to flex-start, the items will line up at the start of the flex-container (and they will be as high as the content if height is not set). If you set align-items to flex-end, you can align the items to the end of the flex container, or center to align them in the center.

**justify-content** property is used to align items on the MAIN AXIS, the direction in which flex-direction has set the flow. The initial value is flex-start which will line the items up at the start edge of the container, set it to flex-end to line them up at the end, or center to center them. If you use SPACE-BETWEEN the items will take all the spare space and share it evenly so that there will be an equal amount of space between each item (and the first and last items will touch the container). SPACE-AROUND will cause an equal amount of space on the right and left of each item (so between container and first and last item there will be half a space). SPACE-EVENLY will give the items a full size space on either end.

**align-content** controls multilines on the cross axis, has same values as justify-content
when there is only ONE LINE align-content has NO EFFECT

JUSTIFY ITEMS PROPERTY IS IGNORED IN FLEXBOX LAYOUTS
