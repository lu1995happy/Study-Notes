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

