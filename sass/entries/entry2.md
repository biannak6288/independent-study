<center><h1>Entry 2: Rules of Sass</h1></center>
<p>In order to increase my knowledge of SASS, I took courses on <strong>CodeAcademy</strong>. The practices and important lessons provided by this website helped me in the process of learning Sass, as well as helped me become more comfortable with the language. While taking Codecademy lessons, I learned a few basic rules.</p>
<h2>The @-Rules</h2>
<p>The @-Rules in Sass are backbone features that everyone who is interested in learning about Sass needs to know. Some of these @-rules are also extensions of CSS @-rules while others are Sass specific directives.</p>

<h3>@import</h3>
<p>Sass extends the CSS @import rule so it can import SCSS/Sass files. Normally we use this rule to import our Sass into one master file. We include this master file as our main CSS file in a project to use all of the consolidated rules. Importing a file gives access to any mixins or variables included in the files.</p>
<p><code>@import</code> looks for a Sass file to import but will compile to a CSS @import rule under the following conditions:</p>
<li>The file extension is .css
<li>The filename begins with htp://
<li>The filename is a url()
<li>The @import has media queries
<p>If the extension of the file is .scss or .sass the file will be imported. If there is no extension Sass will try and find a file that matches the name and the proper extension. For example:</p>
<center><code>@import "sample.scss";</code></center>

<center><code>@import "sample";</code></center>
<p>Both of these @import statements are valid and will import the sample.scss file. The second import would also import sample.sass if it existed. We can also import multiple files in one @import statement by including the files in a comma separated list.</p>
<center><code>@import "sample1", "sample2", "sample3";</code></center>

<center>**Care must be taken when importing files, as they must be imported in a correct order.**</center>

<h3>@media</h3>
<p><code>@media</code> behaves the same as CSS @media rules with the exception that they can be nested inside of CSS rules. When @media directives are nested in CSS rules, they will be at the top level of the stylesheet.</p>
<code>
      .container { <br>
       width: 60%; <br>
       @media (min-width: 200px) and (max-width:600px) { <br>
       width: 100%; <br>
       } <br>
    }
</code>
<p>Will compile to this:</p>
<code>
.container { <br>
  width: 60%; <br>
} <br>
@media (min-width: 200px) and (max-width: 600px) { <br>
  .container { <br>
    width: 100%; <br>
  } <br>
} 
</code>
<p>There is a separate rule for the media query even though it was nested inside of the <code>.container</code> class. We can also nest @media queries inside of another. The queries will be combined using <code>and</code>.</p>
<code>
@media screen and (max-width: 600px) { <br>
  .main { <br> 
    width: 100%; <br>
  } <br>
} <br>
@media screen and (min-width: 700px) {<br>
  .main {<br>
    width: 70%;<br>
  }<br>
}
</code>

<h3>@extend</h3>
<p>Sometimes when styling a page you may have an element that should have all the styles of another element as well as styles of its own. we can use Sass to lessen the amount of typing we have to do. The <code>@extend</code> directive allows us to have one element inherit the styles of another.</p>
<code>
.master { <br>
  color:  black;<br>
  font-size: 12px;<br>
}<br>
.emphasis {<br>
  @extend .master;<br>
  font-weight: bold;<br>
}
</code>
<p>I used <code>@extend</code> to rewrite the styles from above and as a result gave me:</p>
<code>
.master, .emphasis { <br>
  color: black;<br>
  font-size: 12px;<br>
}<br>
<br>
.emphasis {<br>
  font-weight: bold;<br>
}
</code>
<p>As you can see <code>.emphasis</code> is included with <code>.master</code> as well as having styles that only apply to emphasized text.</p>
<p>With the @extend directive we can extend complex selectors, have multiple @extends, chain @extends, and do many more wonderful things with our code.</p>

<h3>@at-root</h3>
<p>The @at-root directive creates rules at the root of the document instead of being nested in their parent element.</p>
<code>
.top { <br>
  .first {<br>
    font-size: 12px;<br>
  }<br>
  @at-root {<br>
    .second {<br>
      font-size: 14px;<br>
    }<br>
    .third {<br>
      font-size: 16px;<br>
    }<br>
  }<br>
  .fourth {<br>
    font-size: 18px;<br>
  }<br>
}
</code>
<p>Which compiles to:</p>
<code>
.top .first {<br>
  font-size: 12px;<br>
}<br>
.second {<br>
  font-size: 14px;<br>
}<br>
.third {<br>
  font-size: 16px;<br>
}<br>
.top .fourth {<br>
  font-size: 18px;<br>
}
</code>
<p>The @at-root directive works on a single line or a block of selectors. However, the selectors nested inside @at-root are at the root of the document. The other selectors are nested inside <code>.top.</code> The @at-root directive also allows you to move outside of directives by using <code>without:...</code> or <code>with:...</code>.</p>

<h3>@debug</h3>
<p>The <code>@debug</code> directive prints the value of a Sass expression to the standard error output stream. For example:</p>
<center><code>@debug 10px + 20px;</code></center>
<p>When the fileis saved, the output is written to the output stream of my watch command.</p>
<center><code>1 DEBUG: 30px</code></center>

<h3>@warn</h3>
<p>The <code>@warn</code> directive prints the value of a Sass expression to the standard error output stream.</p>
<code>
$wrn: 20px; <br>
@warn "#{$wrn}";
</code>
<p>THis rule will allow for the display of the value of the expression as well as the line number of the warning.</p>

<h3>@error</h3>
<p>The <code>@error</code> directive gives the value of a Sass expression as an error. This also goes to the standard error stream</p>
<code>
$test: 1px; <br>
@error "#{$test}";
</code>
<p>This rule will display the error, line number, and value in the standard error stream.</p>

<p>Although coding without <strong>Sass</strong> is very possible, implementing it into our code will make our process much more efficient.</p>

<h2>Takeaways</h2>
<li>Keep training with these rules because they will assist with learning Sass faster
<li>Search more ways to efficiently learn the language
<li>Keep practicing all aspects I learned in Sass so I don't forget them
<li>Remain motivated to learn new things!!


