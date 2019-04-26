# CSS Coding Questions

## How to display two inner div in a line

```css
// 1
display: flex

// 2
display: inline

// 3
display: inline-block

// 4
float: left
float: right
```

## Write some HTML code to show the below CSS rules

```css
[role=sidebar] > ul li:not([link^=mailto]) {
    display: inline-block;
}
```

```markup
<div role="sidebar">
    <ul>
        <li link="mailto"></li>
        <li link="mailto1"></li>
        <li>3</li>
        <li>4</li>
    </ul>
</div>
```

## Write some CSS code for 4 different screen types

![](../.gitbook/assets/image%20%286%29.png)

```markup
<h4>Question:
  Pls write css for these 4 divs to adapt <i>3 different screen</i>.<br>
phone: screen smaller than 600px<br>
tablet: screen size between 600px and 768px<br>
Desktop: screen larger than 768px<br>
  <p>You can find the example picture <a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2013/06/figure112.png">here</a> </p>
</h4>
<div class="container">
  <div class="green col">green</div>
  <div class="red col">red</div>
  <div class="blue col">blue</div>
  <div class="yellow col">yellow</div>  
</div>
```

```css
.container {
  width: 100%;
  height: 200px;
  display: flex;
  flex-wrap: wrap;
}
.green { 
  background: green;
}

.red {
  background: red;
}
.blue {   
  background: blue;
}
.yellow {  
  background: yellow;
}

@media screen and (max-width: 600px) {
.col {
  width: 100%;
}

}
@media only screen and (min-width: 600px) {
  .col {
    width: 50%;
  }
}

@media only screen and (min-width: 768px) {
  .col {
    width: 25%;
  }
}
```

## Newspaper Layout

![](https://lh4.googleusercontent.com/zTQjlH2xgU9gmlSiw4WqwcAHSQWKlzzi7hOy-MOM_AU_9L2lUIw04LQdjSMfWnu3TU5hPDk2ncG699DwDx-QXxlrmuJQRuyKFPNTPo0t5XY31j2BjbMJFqtzk5mExsGuVNd2NLXH9NN-4llxbQ)

```markup
<div class="container">
  <header> Header </header>
  <aside> Aside </aside>
  <section> 
    <div class="content1"> 1 </div>
    <div class="content2"> 2 </div>
  </section>
  <article> Article </article>  
</div>
```

```css
* {
  box-sizing: border-box;
}

.container {
  width: 50vw;
  height: 80vw;
  border: solid;
  position: relative;
}

header {
  text-align: center;
  border-bottom: dotted;
  height: 3vw;
  line-height: 3vw;
}

aside {
  width: 10vw;
  height: 77vw;
  border-right: dotted;
  line-height: 77vw;
  text-align: center;
  float: left;
}

section {
  position: absolute;
  width: 40vw;
  height: 38.5vw;
  border-bottom: dotted;
  right: 0;
}

div.content1, div.content2 {
  height: 38.5vw;
  width: 20vw;
  float:left;
  line-height: 38.5vw;
  text-align: center;
}

div.content1 {
  border-right: dotted;
}

article {
  height: 38.5vw;
  width: 40vw;
  position: absolute;
  bottom: 0;
  right: 0;
  line-height:38.5vw;
  text-align: center;
}
```

## Design a nav bar using HTML and CSS

```markup
<ul>
  <li><a href="#home">Home</a></li>
  <li><a href="#news">News</a></li>
  <li><a href="#contact">Contact</a></li>
  <li style="float:right"><a class="active" href="#about">About</a></li>
</ul>
```

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* Change the link color to #111 (black) on hover */
li a:hover {
  background-color: #111;
}

.active {
  background-color: #4CAF50;
}
```

## Using LESS to display the layout

![](../.gitbook/assets/image%20%282%29.png)

## Add animation to change the height 

```css
<style>
    div {
        animation: changeHeight 5s;
    }
    @keyframes changeHeight {
        from {
            height: 0px;
        }
        to {
            height: 100px;
        }
    }
</style>

<body>
    <div>Absolute</div>
</body>
```

