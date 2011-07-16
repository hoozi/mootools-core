Slick {#Slick}
==========================

Slick is the selector engine used by MooTools. It supports many CSS3 selectors and more!

### See Also:

- [W3C Pseudo Classes](http://www.w3.org/TR/2005/WD-css3-selectors-20051215/#pseudo-classes)


Reversed Combinators
-------------------------------------

Reversed Combinators redirect the flow of selectors and combinators. Slick implements these by prepending `!` to a selector or combinator.

### Examples:

	$$('p ! div')		// A <div> that is an ancestor of a <p>
	$$('p !> div')		// A <div> that is a direct parent of a <p>
	$$('.foo !+ p')		// Gets the previous adjacent <p> sibling

### Notes:

Reversed Combinators are used internally by MooTools for many of our traversal methods. They offer an extremely concise and powerful alternative to traversal methods like `getParent()`.


Slick.definePseudo
-------------------------------------

definePseudo allows you to create your own custom pseudo selectors.

### Examples:

	Slick.definePseudo('my-custom-pseudo', function(){
		// 'this' is the node to check
		return document.id(this).retrieve('something-custom').isAwesome;
	});
	
	$$(':my-custom-pseudo')		// Will return the first <p> tag that is awesome
	
	Slick.definePseudo('has-color', function(color){
   		return document.id(this).getStyle('color') == color;
	});
	
	<p style="color: red">foo</p>
	<p style="color: blue">bar</p>
	
	$$(':has-color(red)');		// Will return the first <p> tag


Selector: Next Siblings ('~') {#Selector:nextsiblings}
-------------------------------------

Gets the next siblings.

### Example:
	
	$$('p.foo ~')		 // Gets all next siblings of <p class='foo'>
	$$('p.foo ~ blockquote') // Gets every <blockquote> with a <p class='foo'> sibling somewhere *before* it


Selector: Previous Siblings ('!~') {#Selector:previoussiblings}
-------------------------------------

Gets the previous siblings.

### Example:
	
	$$('p.foo !~')            // Gets all previous siblings of <p class='foo'>
	$$('p.foo !~ blockquote') // Gets every <blockquote> with a <p class='foo'> sibling somewhere *after* it
	

Selector: All Siblings ('~~') {#Selector:allsiblings}
-------------------------------------

Gets all siblings.

### Example:

	$$('p.foo ~~')            // Gets all previous and next siblings of <p class='foo'>
	$$('p.foo ~~ blockquote') // Gets every <blockquote> with a <p class='foo'> sibling before OR after it

Selector: First Child ('^') {#Selector:firstchild}
-------------------------------------

Gets the first child of an element.

### Example:

	$$('p.foo ^')		// Gets the first child of <p class='foo'>
	$$('p.foo ^ strong')	// Gets every <strong> that is the first element child of a <p class='foo'>


Selector: Last Child ('!^') {#Selector:lastchild}
-------------------------------------

Gets the last child of an element.

### Example:

	$$('p.foo !^')		// Gets the last child of <p class='foo'>
	$$('p.foo ^ strong')	// Gets every <strong> that is the last element child of a <p class='foo'>



Selector: checked {#Selector:checked}
-------------------------------------

Matches all Elements that are checked.

### Examples:

	$$(':checked')

	$('myForm').getElements('input:checked');


Selector: enabled {#Selector:enabled}
-------------------------------------

Matches all Elements that are enabled.

### Examples:

	$$(':enabled')

	$('myElement').getElements(':enabled');
	

Selector: empty {#Selector:empty}
---------------------------------

Matches all elements which are empty.

### Example:

	$$(':empty');


Selector: contains {#Selector:contains}
---------------------------------------

Matches all the Elements which contains the text.

### Variables:

* text - (string) The text that the Element should contain.

### Example:

	$$('p:contains("find me")');


Selector: focus {#Selector:focus}
---------------------------------------

Gets the element in focus.

### Example:

	$$(':focus');		// Gets the element in focus


Selector: not {#Selector:not}
-------------------------------------

Matches all elements that do not match the selector.

<small>Note: The Slick implementation of the `:not` pseudoClass is a superset of the standard. i.e. it can do more stuff.</small>

### Examples:

	$$(':not(div.foo)'); // all elements except divs with class 'foo'

	$$('input:not([type="submit"])'); // all inputs except submit buttons

	myElement.getElements(':not(a)');

	$$(':not(ul li)');


Selector: nth-child {#Selector:nth-child}
-----------------------------------------

Matches every nth child.

### Usage:

Nth Expression:

	':nth-child(nExpression)'

### Variables:

* nExpression - (string) A nth expression for the "every" nth-child.

### Examples:

	$$('#myDiv:nth-child(2n)'); //Returns every even child.

	$$('#myDiv:nth-child(n)'); //Returns all children.

	$$('#myDiv:nth-child(2n+1)') //Returns every odd child.

	$$('#myDiv:nth-child(4n+3)') //Returns Elements 3, 7, 11, 15, etc.


Every Odd Child:

	':nth-child(odd)'

Every Even Child:

	':nth-child(even)'

Only Child:

	':nth-child(only)'

First Child:

	'nth-child(first)'

Last Child:

	'nth-child(last)'

### Note:

This selector respects the w3c specifications, so it has 1 as its first child, not 0. Therefore nth-child(odd) will actually select the even children, if you think in zero-based indexes.


Selector: even {#Selector:even}
-------------------------------

Matches every even child.

### Example:

	$$('td:even');

### Note:

This selector is not part of the w3c specification, therefore its index starts at 0. This selector is highly recommended over nth-child(even), as this will return the real even children.


Selector: odd {#Selector:odd}
-----------------------------

Matches every odd child.

### Example:

	$$('td:odd');

### Note:

This selector is not part of the w3c specification, therefore its index starts at 0. This selector is highly recommended over nth-child(odd), as this will return the real odd children.


Selector: index {#Selector:index}
-----------------------------

Matches the node at the specified index

### Example:

	$$('p:index(2)');		// Gets the third <p> tag.

### Note:

This is zero-indexed.


Selector: first-child {#Selector:first-child}
---------------------------------

Matches the first child.

### Usage:

	':first-child'

### Example:

	$$('td:first-child');


Selector: last-child {#Selector:last-child}
-------------------------------------

	Matches the last child.

### Usage:

	':last-child'

### Example:

	$$('td:last-child');


Selector: only-child {#Selector:only-child}
-------------------------------------

Matches an only child of its parent Element.

### Usage:

	':only-child'

### Example:

	$$('td:only-child');



[Slick]: /core/Slick/Slick