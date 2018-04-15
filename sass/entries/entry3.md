# Entry 3: Mixins, Conditionals, and Loops
For my third week of Independent Study, I continued exploring guidelines to learning SASS. Last week, I conquered understanding the rules SASS engneders, however, this week I will focus predominantly on three categories: <b>mixins</b>, <b>conditionals</b>, and <b>loops</b>. I am excited to continue my journey in SASS because it has been an interesting one, which continuously allows me to explore new aspects to further my knowledge of coding in general.
Anyway, enough with this weeks introduction, lets get into what I had learned this week!

## What is a ```Mixin```...
```Mixins``` are one of the most used features out of the entire Sass language. They are the key to reusability and <b>D</b>on't <b>R</b>epeat <b>Y</b>ourself components. Afterall, mixins allow authors to define styles that can be reused throughout the stylesheet without needing to resort to regular classes such as ```.float-left```.

They can contain full CSS rules and much of everything that is allowed in a Sass document. Furthermore, mixins can even take arguments in, just like functions. Needless to say, the possibilities are endless with the use of mixins.

However, it is important to remember that one cannot abuse the power of mixins. Shall I remind you that the keyword needed to continuously repeat to yourself here is *simplicity*. When working with this part of the code, don’t over think your code; keep it simple. If one of your mixins exceeds 20 lines, then it should be either split into smaller chunks or completely revised.

#### Mixin Basics
Mixins are extremely powerful. That being said, lets get into the details.

In this case, you will use the rule of thumb, which is that if you happen to spot a group of CSS properties that always 
appear together for a reason, you can put them in a mixin instead. This is an example of a group of CSS properties which
appear together and form an argumentless mixin:
```
@mixin clearfix {
  &::after {
    content: '';
    display: table;
    clear: both;
  }
}
```
Another valid example would be a mixin to size an element, defining both ```width``` and ```height``` 
at the same time. Not only would it make the code much easier and faster to type, but also more legible.
```
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}
```
#### More On Argument-less Mixins
Sometimes mixins are used only to avoid repeating the same group of declarations after 
one another, yet do not need any parameter or have sensible enough defaults so that 
we don’t necessarily have to pass arguments.

In such cases, we can safely omit the parentheses when calling them. The ```@include``` 
keyword already acts as a indicator that the line is a mixin call, therefore there is 
no need for extra parentheses here.
```
// Hello
.foo {
  @include center;
}

// Goodbye
.foo {
  @include center();
}
```
#### Arguments List
When dealing with an unknown number of arguments in a mixin, always use an <b>arglist</b> 
rather than a regular list. Think of an arglist as the 8th hidden undocumented data type from Sass 
that is implicitly used when passing an arbitrary number of arguments to a mixin or a 
function whose signature contains ....
```
@mixin shadows($shadows...) {
}
```
Now, when building a mixin that accepts a handful of arguments, make sure to think twice 
before merging them out as a list or a map thinking it will be easier than passing them 
all one by one.

Sass is actually pretty clever with mixins, so much so that you can actually pass a list
or a map as an arglist to a function/mixin so that it gets parsed as a series of 
arguments.

#### Mixins and Vendor Prefixes
It might be tempting to define custom mixins to handle vendor prefixes for unsupported 
or partially supported CSS properties. However, we do not want to do this. First, if you 
can use <b>Autoprefixer</b>. It will remove Sass code from your project, it will 
always be up-to-date and finally will necessarily do a much better job than you at prefixing 
code.

However, if you caanot use Autoprefixer, and only when you can't, thats when you can have 
your own mixin for prefixing CSS properties. Do not build a mixin per property, meaning manually 
printing each vendor.
```
// Goodbye
@mixin transform($value) {
  -webkit-transform: $value;
  -moz-transform: $value;
  transform: $value;
}
```
Do it the easier way...
```
@mixin prefix($property, $value, $prefixes: ()) {
  @each $prefix in $prefixes {
    -#{$prefix}-#{$property}: $value;
  }

  #{$property}: $value;
}
```
Using this mixin should be pretty straightforward...
```
.foo {
  @include prefix(transform, rotate(90deg), ('webkit', 'ms'));
}
```
<b>Though this is a solution, it isn't the best one that could be created with mixins</b>

## What are Conditional Statements...
You probably already know that Sass provides conditional statements via the ```@if``` and ```@else``` 
directives. Unless you have some medium to complex logic in your code, there is no 
need for conditional statements in your everyday stylesheets. Afterall, they mainly 
exist for *libraries* and *frameworks*.

However, if you ever find yourself in need of them, please respect the following 
guidelines:
* No parentheses unless they are necessary
* Always an empty new line before ```@if```
* Always a line break after the opening brace (```{```)
* ```@else``` statements on the same line as previous closing brace (```}```)
* Always an empty new line after the last closing brace (```}```) unless the next line is a closing brace (```}```)
```
// Hello
@if $support-legacy {
  // …
} @else {
  // …
}

// Goodbye
@if ($support-legacy == true) {
  // …
}
@else {
  // …
}
```
When testing for a false value, always use the <b>not</b> keyword rather than testing against 
<b>false</b> or <b>null</b>:
```
// Hello
@if not index($list, $item) {
  // …
}

// Goodbye
@if index($list, $item) == null {
  // …
}
```
<b>Always put the variable part on the left side of the statement, and the (un)expected 
result on the right. Reversed conditional statements often are more difficult to read, 
especially to unexperienced developers.</b>
```
// Yep
@if $value == 42 {
  // …
}

// Nope
@if 42 == $value {
  // …
}
```
Moving along, when using conditional statements within a function to return a different
result based on some condition, always make sure the function still has a ```@return``` 
statement outside of any conditional block. For example,
```
// Hello
@function dummy($condition) {
  @if $condition {
    @return true;
  }

  @return false;
}

// Goodbye
@function dummy($condition) {
  @if $condition {
    @return true;
  } @else {
    @return false;
  }
}
```
## Loops are...
The overall presence of loops usually implies moderately complex logic that probably 
does not belong to Sass. Before using a loop, make sure it makes sense and that it 
actually solves an issue!
#### Each
The ```@each``` loop is definitely the most-used out of the three loops provided by 
Sass. It provides a clean API to iterate over a list or a map.
```
@each $theme in $themes {
  .section-#{$theme} {
    background-color: map-get($colors, $theme);
  }
}
```
When iterating on a map, always use ```$key``` and ```$value``` as variable names to enforce consistency.
```
@each $key, $value in $map {
  .section-#{$key} {
    background-color: $value;
  }
}
```
Be sure to respect the following guidelines to preserve readability:
* Always have an empty new line before ```@each```
* Always have an empty new line after the closing brace (```}```) unless the next line 
is a closing brace (```}```).

#### For
The ```@for``` loop might be useful when combined with CSS’ <b>:nth-*</b> pseudo-classes. Except 
for these scenarios, prefer an ```@each``` loop if you have to iterate over something.
An example of a ```@for``` loop is:
```
@for $i from 1 through 10 {
  .foo:nth-of-type(#{$i}) {
    border-color: hsl($i * 36, 50%, 50%);
  }
}
```
Always use ```$i``` as a variable name to stick to the usual convention and unless you 
have a really good reason to, never use the to keyword: always use through. Many 
developers do not even know Sass offers this variation; using it might lead to 
confusion.

Also be sure to respect those guidelines to preserve readability:
* Always have an empty new line before ```@for```
* Always have an empty new line after the closing brace (```}```) unless the next line
is a closing brace (```}```)

#### While
The ```@while``` loop has absolutely no use case in a real Sass project, 
especially since there is no way to break a loop from the inside. *Do not use it.*
<br>
<br>

Sadly we have come to the end of our tutorial. Now it is time to reflect on what we have learned! Les get into the ```takeaways...```

## Takeaways
* Don't forget to put the variable part on the left side and the (un)expected result on the right side
* The loop that you should be using most of the time, if not at all times, is the ```@each``` loop
* The ```@while``` loop is pointless in this case, forget about it!
* If you see a group of ccc properties clumped together, then you have the ability to put it into a mixin
* Remember to keep your code organized so that it makes sense to you and others who are learning from it







