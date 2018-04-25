# Entry 4: Functions and Nesting
This is my fourth week of learning SASS, and possibly my hardest one because I don't have 
as much time to learn as I would ina a typical week, due to the fact that I am going on a senior trip with my 
graduating class. However, that doesn't mean that I will not be creating an entry or keeping track of 
my learning because that is as important. Throughout the four weeks that I have engaged in this
coding language, I learned several concepts of SASS which can help me understand the world better as well. 
I learned to be confident and concise with everything that I do, whether it has to do with 
wriitng code or just my daily life. I am happy that this coding language was able to bring
about such an immense impact on my software enginering career and my life.

**_Well, lets not waste anymore times and get into the entry..._**

## Functions
A **function** has an output with a single value. This single value could be any SASS data type including: 
a number, string, color, boolean, or list.

**TIP:** Functions should be utilized to calculate a value that may be reused somewhere else in the code!

Functions can accept numerous amounts of arguments starting with one and going all the way to infinites. Here is 
an example of a two-argument function:

```CSS
@function my-calculation-function($first-number, $second-number) {
    @return $first-number + $second-number
}
```
**the two arguments accepted by the function here are: ```$first-number```, and ```$second-number```
and the value returned by the function are those 2 variables added together.

*Moving along to the layout portion of functions...*

A certain formula has been established to calculate the percent value for a width so that we as programmers
can achieve a **fluid layout** based on a reference design made using pixels.
```CSS
target / context = result
```
Lets use this formula in an actual case. So if there is a container that is 1000px wide, and 
a module designed to be 850px wide, which leads to a calculation of:
```CSS
850px / 1000px = 85%
```
This easy function helps beginner programmers understand it better, however, it would take 
much longer to submit all functions, therefore we can create another more complex function, like so:
```CSS
@function calc-percent($target, $container) {
    @return ($target / $container) * 100%;
}
```
**TIP:** Always create short names for functions becasue they will be used often, and it is much
faster to type in a shorter name rather than a long one

For example, for the above function I used a decently long name for it, therefore I decided to
show you what not do. However, below I re-wrote the function and used a shorter name, cp instead
of calc-percent:
```CSS
@function cp($target, $container) {
    @return calc-percent($target, $container);
}
```
Finally, with that being out of the way, we can now focus on actually writing SASS with the values
we have already found. Type this:
```CSS
.my-module {
    width: calc-percent(850px, 1000px);
}
```
or, with a shorter function name:
```CSS
.my-module {
    width: cp(850px, 1000px);
}
```
Remember these are written in **SASS**, but if translated into CSS, which is what most beginner 
programmers are more familiar with, these functions would look like this:
```CSS
.my-module {
    width: 85%
}
```
Although this is a simple example, it is quite useful to see something like this work for a 
beginner programmer. This is great especially because any programmer would rather have SASS do 
their math calculations, rather then do them themself.

<img src= "https://futurestud.io/blog/content/images/2014/Jun/sass-vs-scss.png" />
<center>*Photo Credits: Future Studio*</center>



## Nesting
One reason we may use a preprocessor is to lessen the amount of typing we need to 
create CSS rules. Nesting allows us to use shortcuts to create our rules. The problem 
with all great tools is that the potential for misuse is always there. Nesting is no 
different as overuse can create complex, unmanageable stylesheets.

### What is it exactly?
Nesting allows you to write selectors that mimic the structure of your HTML. 
This allows you to use shortcuts to create your CSS. For example: 
```CSS
div {
    p {
        color: black;
    }
}
```
This is nesting at its simplest. The ```div``` element encloses the ```P``` element. 
This will in turn compile to.
```CSS
div p { color: black; }
```
The ```div``` could also be given its own properties.
```CSS
div {
    font-size: 14px;
    p {
        color: black;
    }
}
```
This in turn compiles to two separate rules, one for the ```div``` by itself and 
another for the ```p``` element inside of the ```div```. For example:
```CSS
div { font-size: 14px;}
div p { color: black; }
```
Nesting styles are **simple** enough. You just enclose a selector (or selectors) 
inside the curly braces of another selector.

Nesting can extend as many levels deep as you wish. What this means is that you can 
nest elements inside of an element that is in turn nested inside another element.
An example of this is...
```CSS
.level_1 {
    .level_2 {
        .level_3 {
            .level_4 {
            }
        }
    }
}
```
**There is really no limit to the amount of levels deep that you can nest elements. 
The main thing to remember is **just because you can do something does not mean you should.** 
It is generally a good idea to not nest deeper than three levels. Anything more than 
that starts to affect the readability of the code. Sass is there to help us write CSS 
faster, not to create a bunch of styles that are not maintainable.** 

For example:
```CSS
.page {
    font-family: sans-serif;
    .content {
        background-color: black;
        .text {
            color: white;
            font-size: 12px;
            .headline {
                font-weight: bold;
                a {
                    color: blue;
                    &:visited {
                        color: green;
                    }
                    &:hover {
                        color: red;
                    }
                    &:active {
                        color: yellow;
                    }
                }
            }
        }
    }

}
```
A look at the compiled output illustrates the problems with nesting too deep.
```CSS
.page { font-family: sans-serif; }

.page .content { background-color: black; }

.page .content .text { color: white; font-size: 12px; }

.page .content .text .headline { font-weight: bold; }

.page .content .text .headline a { color: blue; }

.page .content .text .headline a:visited { color: green; }

.page .content .text .headline a:hover { color: red; }

.page .content .text .headline a:active { color: yellow; }

```
This presents a problem if we change the structure one of our webpages. Lets say we 
changed ```.content``` to ```.article.``` All underlying classes will have to be re-written as 
they are all dependent on being inside ```.content```.

We also have problems with the rules we are creating being useful in only one part of 
our code. If we wanted to use the styles for ```.text``` somewhere else on our site we wouldn't 
be able to since ```.text``` is bound to the elements that enclose it.

## Takeaways
* Do not nest deeper than three levels; it is pointless because the structure becomes too 
complicated and it becomes more difficult to fix a problem later on if it occurs
* Like Mr. Mueller always says: "Quality over Quantity"
* Keep practicing with arguments and functions or else you will never learn how they work
* Functions have many parts to them and if one wants to understand every aspect, they need
* to continuously utilize them in their code, so keep TINKERING
* Functions could have several arguments, not just 1
* Increase your understanding of functions and nesting by practicing in your spare time

UNTIL NEXT TIME...