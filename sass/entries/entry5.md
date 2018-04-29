# Entry 5: File Imports, Operators and Control Structures
This is the fifth week we have been learning together. It has been hard, but I think that we
have been able to gain a lot of interesting knowledge which we can later use in this field
of software engineering or for hobby purposes.

Learning SASS in such a short period of time helped me realize that I am a quick learner 
and that I am far more capable learning things on my own then when it is taught to me. I
believe that by self-educating myself, I learn responsibility for my own learning and 
understand the meaning of time management. 

Well, now that I have reflected on my experience of learning so far, lets get into the 
learning for this week. This week we will be diving into the world of file imports, operators,
and control structures. Enjoy!

## File Imports
**I have done an entry on all SASS bsaic rules (i.e. @import) and therefore this section will be basically re-iterating
them and how they generally work**

SASS has the ability to include one file in another, similar to ```include()``` and ```require()```. 
In SASS, you use @import *PATH/TO/FILE* to include another (second) file. These files that are **included**, which 
are called **partials**, can be used to organize your SASS code into multiple partials, where each is named for its own 
purpose. For example, you may have a partial called *‘typography’* and another called *‘forms.’*

If you look at how a SASS library is structured, it generally has one file for setting up global variables and another file for 
including components. For example, this settings partial in Foundation sets up the global functions, while the main file includes 
the partial along with the rest of the component-specific partials.

Partials tend to get used containers for reusable code. For example, there is one partial for setting up all 
of the variations on the main colors including the tints, shades, and complements. I could copy this same file into each of my 
projects and *import* it directly after defining the color palette.

## Operators
Like other programming languages, SASS provides a basic mathematical operator. 

If you would want to set an element to have a width that is half of a defined variable, say $max-width. You can just divide 
$max-width by 2. For example, here is a simple grid system.
```CSS
$row-width = 1200px;
.row {
	max-width: 1200px;
}
 
.row .half {
	display:inline;
	float:left;
	width: $row-width/2;
}
 
.row quarter {
	display:inline;
	float:left;
	width: $row-width/4;
}
```
And of course, I know that I can reduce the **redundancy** in that code using nesting, but to learn how to do that you should
re-read my entry from last week.

## Control Structures
SASS also provides basic control structures, like if, if/else, each, for, and while, which work the same way as they do in regular
CSS, but with a different syntax.

Lets re-iterate this idea of coniditonals...

```If``` statements are great for use inside of a mixin definition. In this example below, I added a border color to the 
right-tilt-rounded-borders mixin from before, but use an ```if/else``` structure to change the color of the border based on its width.
```CSS
@mixin right-tilt-variable-borders( $width ) {
	@if $width &lt; 3 {
		border-color: $primary;
	}
	@else {
		border-color: $primaryTint;
	}
	border-width: $width;
	@include right-tilt-rounded-borders;
 
}
```
In regular CSS, you would do something like this:
```CSS
function right-tilt-variable-borders( $width ) {
	if ( $width &lt; 3 ) {
		echo 'border-color: '.$primary';
	  }
	else {
		 echo ' border-color: $primaryTint;`
		}
}
```
```For loops``` in SASS work just like for loops in CSS, and are great for creating sequential named classes, or creating scaled 
sizes. For example, here I created a set of classes that increment font size by the golden ratio. Notice that the incremental 
variable, in this case ```$i```, is used as ```#{$i}```, which will output as the current count of the loop (1,2,3, or 4).
```CSS
@for $i from 1 through 4 {
	.gText-#{$i} { font-size: .618em * $i; }
}
```

‘@for $i from 1 through 4’ syntax that sets up the for loop, is the equivalent in CSS to ‘for ( $i = 0; $i <= 4; $i++ ).'

Along with for loops, ```foreach``` loops in CSS are two of the most common ways to avoid writing repetitive code. In SASS, what we
call a foreach loop in CSS, is called an ```each``` loop. To process a comma-separated list of strings in SASS, we define the variable 
to loop through, and then we write a CSS declaration using the variable. We use the same ```#{$variable}``` formatting as in the for 
loop.
```CSS
@each $city in Pittsburgh, London, Paris, Tokyo {
	.#{$city}-banner {
	background-image: url('/images/#{$city}.png');
  }
}
```

In CSS, the equivalent to ```‘@each $city in Pittsburgh, London, Paris, Tokyo’``` would be:
```CSS
$cities = array( 'Pittsburgh', 'London', 'Paris', 'Tokyo' );
foreach ( $cities as $city )
```

In both our *for* and *each* loops examples, we were able to write one CSS declaration in place of four. Of course, since 
these control structures can be used for a practically infinite number of iterations, you can see how they are a key component 
to how SASS can free us from writing repetitive CSS.

# Takeaways
* Always remember the correct syntx for the language you are coding in because differnet languages and/or programs require 
different syntax to work
* Keep tinkering with all these rules and conditionals so that you would know them by heart or else you would not be able
to run your own program as easily
* Maintain a calm and positive mindset so that your work will go further and not remain in one spot
* Keep re-reading these entries to help you understand aspects of SASS in case you would forget while coding

Stay tuned for next week!!











