<center><h1>Entry 1: Introduction</h1></center>

<p>I am currently a senior at the High School of Telecommunications Arts and Technology, and for my final project in the software engineering class, I will begin a journey of learning on my own.</p>
<h3>How I Chose My Topic</h3>
<p>After researching various topics that I could potentially explore for teh next nine weeks, I narrowed my list down to two: Sass and CyperSecurity. Ultimately, I decided to choose Sass because this topic would challenge me as a software engineer and it will assist me with making my previous projects more complex and interesting. Afterall, this language will allow me to learn many valuable skills that might not be too challenging, but that would help me in my future coding endeavors. During most of these nine weeks, I'm expecting myself to be in the "learning zone," because it will be the first time that I will be experimenting with learning a topic on my own, of my own choice. I am really excited to begin this new path of learning, and I can't wait to see the end result. </p>
<h3>What is Sass?</h3>
<p>Sass stands for Syntactically Awesome Style Sheets and was  designed and created by Hampton Catlin. Sass manipulates CSS using variables, mixins, inheritance and nesting rules. Given the extensions .sass and .scss respectively, it’s translated to well-formatted CSS using a command line tool or web-framework plugin. Sass makes it easier to write less CSS codes and manipulate them dynamically. It’s a great way to write more functional CSS codes and can speed up the workflow of every web developer and designer.</p>
<p>For example, in CSS, I used a header tag and put a zero value for margin and padding then white color for its text color:</p>
<center><code>
    header {
     margin: 0;
     padding: 0;
     color: #fff;
    }
</code></center>
<p>However, in Sass, I would write the same code, but using more symbols rather than numbers which will make the code more concise.</p>
<center><code>
    $color:  #fff;
    header {
    margin: 0;
    padding:0;
    color: $color;
}
</code></center>
<p>I will use a variable $color and give it a hexadecimal color value of #fff for white color. And then under the CSS style, instead of putting a hexadecimal color value of #fff, use the variable $color that was set in the beginning of the code.</p>

<h3>Since I spoke of variables, lets continue...</h3>
<p>Sass variables are declared using the $ character and are defined like CSS values. Using Sass, you can declare variables for styles like font size, margin, padding and many others. Using variables and giving it a style value makes it easy to reuse a style repeatedly.</p>
<p>There are six different types of variables you can use with Sass:</p>
<ul>
    <li>Strings (e.g. $myString: “your text here”;)</li>
    <li>Numbers (e.g. $myNum: 10px;)</li>
    <li>Colors (e.g. $myColor: white;)</li>
    <li>Booleans (e.g. $myBool: true;)</li>
    <li>Lists (e.g. $myItemList: 1px solid red;)</li>
    <li>Nulls (e.g. $myVar: null;)</li>
</ul>
<p>Here is what it looked like when I put it into practice</p>
<center><code>
$myColor: #009a82;
$myString: " some text here ";
$myFontSize: 13px;
$myMargin: 0px auto;
$myWidth: 460px;
h1 {
	color: $myColor;
	margin: 0;
	padding: 0;
}
#container {
	width: $myWidth;
	margin: $myMargin;
}
</code></center>
<p>To be honest, there is not much of a difference between regular CSS and SASS, however, those minor changes do their job of making the language more efficient.</p>

<h3>Takeaways</h3>
<li>In order to start learning a new language or topic, I find that it is helpful to start with an easy, self explanatory, example so that you can understand how it works before continuing with something more difficult.</li>
<li>When attempting to make sense of complex code, try breaking it down so that you can understand the function of each part</li>
<li>Google the things that you don't understand because otherwise you will never learn!</li>
<li>Do as much research as you possible can so that you know everything you can possibly know about the topic, or else you will be lost when the more complex code comes along</li>
<li>Don't only look for the HOW in your project, but for the WHY as well.</li>


[Next](entry2.md)
<br>
[Table of Contents](../README.md)
