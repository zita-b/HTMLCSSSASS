BEM (Block, Element, Model) is a component based approach to web-development. The idea behind it is to divide the user interface into independent blocks. this makes interface development easy and fast and it allows reuse of existing code.

BLOCK - a functionally independent page component that can be reused. You shouldn't set margin or positioning for the block. Blocks can be nested.

ELEMENT - a composite part of a block that can't be used separately from it. The structure of an element's full name is block_name__element-name
An element is always part of a block, not another element.

MODIFIER - an entity that defines the appearance, state or behavior of a block or element. The modifier name is separated from the block or element name by a single underscore (_)
block-name_modifier-name(_modifier-value)
block-name__element-name_modifier-name(_modifier-value)

a modifier can't be used alone. A modifier should change the appearance, behavior, or state of the entity, not replace it.

MIX - a technique for using different BEM entities on a single DOM node.
Mixes allow you to combine the behavior and styles of multiple entities without duplicating your code

<!-- `header` block -->
<div class="header">
    <!--
        The `search-form` block is mixed with the `search-form` element
        from the `header` block
    -->
    <div class="search-form header__search-form"></div>
</div>

In this example we have combined the behavior and styles of the search-form block and the search-form element from the header block.
This allows us to set the external geometry and positioning in the header__search-form element, while the search-form block itself remains universal. As a result, we can use the block in any other environment.

FILE STRUCTURE - The implementation of blocks, elements and modifiers are divided into independent technology files, so we have to connect them individually.

- a single block corresponds to a single directory
- the block and the directory have the same name
- the block directory is the root directory for the subdirectories of its elements and modifiers
- names of element directories begin with a double underscore (__)
- names of modifier directories begin with a single underscore (_)
