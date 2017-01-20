# My Coding Style

The following document describes my own writing rules for development.

This repository wasn't created to be a complete coding guide, it's just a way to documentate ~~my OCD~~ and share my coding style to receive contributions and improvements from other developers.

This is a living document and contributions are always welcome!

## Index

1. [Commits](#1-commits)
1. [HTML](#2-html)
1. [Pug](#3-pug)
1. [CSS](#4-css)
1. [SASS](#5-sass)
1. [JavaScript](#6-js)
1. [C++](#7-c)
1. [References](#8-references)
1. [License](#9-license)

## 1. Commits

GitHub is a global website, so our commits must be accessible for everyone. To make easier the contribuction and interaction from anyone in a project, all commit messages, pull requests or issues must to be written in  ~~JavaScript~~ **English**.

You shouldn't use Past or Present Continuous tenses for commit messages, those should be in Imperative Present tense. (It's a [Git recommendation](http://git.kernel.org/cgit/git/git.git/tree/Documentation/SubmittingPatches?id=HEAD#n111))

> And Remember to check if already exists an open issue related to your commit and make references using the hash symbol ('#') on your commit message.

```shell
# Good
git commit -m "Add something on something else"
git commit -m "Add something on something else #42"

# Bad
git commit -m "Added something on something else"
git commit -m "Adding something on something else"
```

## 2. HTML

The main influence for that HTML section rules is the [Code Guide by @mdo](https://github.com/mdo/code-guide).

### HTML Index

1. [HTML Syntax](#21-html-syntax)
1. [HTML Comments](#22-html-comments)
1. [HTML Character Encoding](#23-html-character-encoding)
1. [HTML Attribute Order](#24-html-attribute-order)
1. [HTML Performance](#25-html-performance)
1. [HTML Base Code](#26-html-base-code)

### 2.1. HTML Syntax

Aways use **soft tabs** with **2 spaces width** and be consistent (never mix spaces and tabs).

Important: **Never left trailing spaces** (This Sublime Text plugin can help you -> [Trailing Spaces](https://github.com/SublimeText/TrailingSpaces))

```html
<!-- Good -->
<nav class="navbar">
  <ul class="nav">
    <li class="nav-item">
      <a class="nav-link">

<!-- Bad-->
<nav class="navbar">
    <ul class="nav">
        <li class="nav-item">
            <a class="nav-link">
```

Always use double quotes.

```html
<!-- Good -->
<main class="main">

<!-- Bad-->
<div class='main'>
```

Don't include a `/` in self-closing elements (This isn't XHTML :wink:).

```html
<!-- Good -->
<hr>

<!-- Bad-->
<hr />
```

Separate block elements by a blank line and agroup the inners block elements.

```html
<!-- Good -->
<ul class="nav-tabs">
  <li>...</li>
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ul>

<div class="tab-content">
  ...
</div>

<!-- Bad-->
<ul class="nav-tabs">

  <li>...</li>

  <li>...</li>

  <li>...</li>

  <li>...</li>

</ul>
<div class="tab-content">
  ...
</div>
```

Don't omit optional closing tags

```html
<!-- Good -->
<p>Some text here</p>
<ul class="items">
  <li>My list item</li>
</ul>

<!-- Bad-->
<p>Some text here
<ul class="items">
  <li>My list item
</ul>
```

### 2.2. HTML Comments

Aways add a space between the comment tag and his content.

```html
<!-- This is a good HTML comment -->
<!--This is a bad HTML comment-->
```

### 2.3. HTML Character Encoding

Always use UTF-8 for character encoding.

```html
<head>
  <meta charset="UTF-8">
</head>
```

### 2.4. HTML Attribute Order

HTML attributes should be in this order to facilitate reading.

1. `id`
1. `class`
1. `name`
1. `src`, `for`, `type`, `href`
1. `title`, `alt`
1. `aria-*`, `role`
1. `data-*`
1. modifiers

```html
<a id="open_modal_Link" class="btn" href="#" data-modal="#overlay">

<input class="form-control" type="text">

<img class="img-rounded" src="..." alt="...">
```

### 2.5. HTML Performance

You don't need to specify the type attribute when including CSS or JavaScript files (like `text/css` or `text/JavaScript`).

```html
<!-- Good -->
<link rel="stylesheet" href="assets/css/style.css">
<script src="scripts.min.js"></script>

<!-- Bad -->
<link type="text/css" rel="stylesheet" href="assets/css/style.css">
<script type="text/JavaScript" src="scripts.min.js"></script>
```

For a better performance, all JavaScripts files must be at the end of the code. Before the closing `<body>`.

```html
<!-- Good -->
<script src="scripts.min.js"></script>
</body>

<!-- Bad -->
<script src="scripts.min.js"></script>
</head>
```

Always minify your code (only the build version, of course) in static projects (only HTML). Many tools can make ir easier, like the [html-minifier](https://www.npmjs.com/package/html-minifier) node package.

```html
<!-- Good -->
<html><head>...</head><body>...</body></html>

<!-- Bad -->
<html>
<head>
  ...
</head>
<body>
  ...
</body>
</html>
```

### 2.6. HTML Base Code

The following code is a HTML base for faster start the projects.

> `<head>` and `<body>` tags can be placed at same level as `<html>` tag (for a better readability in bigger projects)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Metadata -->
  <meta charset="UTF-8">
  <meta name="description" content="">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <meta name="format-detection" content="telephone=no">

  <!-- Favicon -->
  <link rel="shortcut icon" href="assets/ico/favicon.ico">

  <!-- CSS -->
  <link rel="stylesheet" href="assets/css/styles.css">

  <!-- Fonts -->
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Open+Sans">

  <!-- Title -->
  <title>Page Title</title>
</head>
<body>
</body>
</html>
```


## 3. Pug

I'm using Pug as main template engine.

### Pug Index

1. [Pug Syntax](#31-pug-syntax)
1. [Pug Comments](#32-pug-comments)
1. [Pug Base Code](#33-pug-base-code)

### 3.1. Pug Syntax

Aways use **soft tabs with 2 spaces width** and be consistent (never mix spaces and tabs).

```pug
//- Good
nav.navbar
  ul.nav
    li.nav-item
      a.nav-link

//- Bad
nav.navbar
    ul.nav
        li.nav-item
            a.nav-link
```

Always use single quotes.

```pug
//- Good
button.btn(data-component='collapse')

//- Bad
button.btn(data-component="collapse")
```

Insert the title of block, separate block element by a blank line and agroup the inners block elements.

```pug
//- Good

//- Header
//- ===================================
header.header(role='banner')
  a.logo(href='#', role='logo')


//- Main
//- ===================================
main.main(role='main')
  section.content

//- Bad
header.header(role='banner')
  a.logo(href='#', role='logo')
main.main(role='main')

  section.content
```

To small elements with only one child, you may prefer the inline pug syntax.

```pug
//- Good
a(href='/'): img(src='assets/img/logo.svg' alt='Logo')

//- Not so good
a(href='/')
  img(src='assets/img/logo.svg' alt='Logo')
```

To small elements consider using the Pug's interpolation syntax.

```pug
//- Good
p Lorem Ipsum #[br] dolor sit amet.

//- Not so good
p
  | Lorem Ipsum
  br
  | dolor sit amet.

//- Bad
p Lorem Ipsum
  br
  | dolor sit amet.
```

### 3.2. Pug Comments

Follow this rule to add comments in Pug.

```pug
//- This is a good example

// This is a bad example
//-This is another bad example
```

Comments using `//-` aren't compiled.

### 3.3. Pug Base Code

The following code is a Basic Pug code for a faster startup.

```pug
include includes/variables

doctype html
html(lang='en')
  head
    //- Metadata
    meta(charset='UTF-8')
    meta(name='description' content='')
    meta(name='viewport' content='width=device-width, initial-scale=1.0, user-scalable=no')
    meta(name='format-detection' content='telephone=no')

    //- Favicon
    link(rel='shortcut icon' href='ico/favicon.ico')

    //- CSS
    link(rel='stylesheet' href='css/style.css')

    //- Fonts
    link(rel='stylesheet' href='https://fonts.googleapis.com/css?family=Open+Sans')

    //- Title
    title Page Title
  body
```


## 4. CSS

This section was mainly influenced by [Code Guide by @mdo](https://github.com/mdo/code-guide).

### CSS Summary

1. [CSS Syntax](#41-css-syntax)
1. [CSS Declaration Order](#42-css-declaration-order)
1. [CSS Class Names](#43-css-class-names)
1. [CSS Performance](#44-css-performance)
1. [CSS Media Queries](#45-css-media-queries)

### 4.1. CSS Syntax

Aways use **soft tabs with 2 spaces width** and be consistent (never mix spaces and tabs).

```css
/* Good */
.nav-item {
  display: inline-block;
  margin: 0 5px;
}

/* Bad */
.nav-item {
    display: inline-block;
    margin: 0 5px;
}
```

Always use double quotes.

```css
/* Good */
[type="text"]
[class^="..."] {
  ...
}

.nav-item::after {
  content: "";
}

/* Bad */
[type='text']
[class^='...'] {
  ...
}

.nav-item::after {
  content: '';
}
```

The opening bracket must to be at same line that the last selector and separated by a single space.

```css
/* Good */
.header {
  ...
}

/* Bad */
.header{
  ...
}

/* Very very bad */
.header
{
  ...
}
```

Always put a single space between a property and his value (and after all colons).

> Alignment: don't align property values, it's look pretty, but is just more work to maintain (and to search)

```css
/* Good */
.header {
  padding: 5rem;
  margin-bottom: 20rem;
}

/* Bad */
.header{
  padding:5rem;
  margin-bottom:20rem;
}

/* Pretty, but bad for maintenance */
.header {
  padding:       5rem;
  margin-bottom: 20rem;
}
```

Include a semi-colon at the end of every declaration. (Even if it's optional)

```css
/* Good */
.header {
  margin-bottom: 20rem;
}

/* Bad */
.header {
  margin-bottom: 20rem
}
```

Keep one selector and declaration per line.

```css
/* Good */
.selector-1,
.selector-2,
.selector-3 {
  color: #fff;
  text-decoration: underline;
}

/* Bad */
.selector-1, .selector-2, .selector-3 {
  color: #fff; text-decoration: underline;
}
```

Single declarations should remain in one line.

```css
/* Good */
.selector-1 { width: 50%; }

/* Bad */
.selector-1 {
  width: 50%;
}
```

Separate each ruleset by a blank line.

```css
/* Good */
.selector-1 {
  ...
}

.selector-2 {
  ...
}

/* Bad */
.selector-1 {
  ...
}
.selector-2 {
  ...
}
```

Use lowercase, shorthand hex values and avoid specifying units in zero-values (because zero is zero, doesn't matters the unit).

```css
/* Good */
.selector-1 {
  color: #aaa;
  margin: 0;
}

/* Bad */
.selector-1 {
  color: #AAAAAA;
  margin: 0px;
}
```

**IMPORTANT:** Nowadays every site must to be accessible for any device, so you should prefer relative units over the absolute ones

### 4.2. CSS Declaration Order

Related property declarations should be grouped together following the order:

1. Positioning
1. Box model
1. Typographic
1. Visual
1. Others

Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles. The box model comes next as it dictates a component's dimensions and placement.

Everything else takes place inside the component or without impacting the previous two sections, and thus they come last.

> I know, in bigger projects with many involved people, it's hard to maintain that order, so, you can use alphabetical order instead (Tip: if you use Sublime Text, just select the lines and press `F9`), the important is keeping a logic.

```css
/* Good (Preferred way) */
.selector-1 {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font-family: "Open Sans", sans-serif;
  font-size: 13px;
  font-weight: normal;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}

/* Good (when it's hard to maintain the first one) */
.selector-1 {
  background-color: #f5f5f5;
  border-radius: 3px;
  border: 1px solid #e5e5e5;
  bottom: 0;
  color: #333;
  display: block;
  float: right;
  font-family: "Open Sans", sans-serif;
  font-size: 13px;
  font-weight: normal;
  height: 100px;
  left: 0;
  line-height: 1.5;
  opacity: 1;
  position: absolute;
  right: 0;
  text-align: center;
  top: 0;
  width: 100px;
  z-index: 100;
}

/* Bad */
.selector-1 {
  font-size: 13px;
  border-radius: 3px;
  background-color: #f5f5f5;
  font-weight: normal;
  opacity: 1;
  position: absolute;
  right: 0;
  border: 1px solid #e5e5e5;
  line-height: 1.5;
  width: 100px;
  top: 0;
  color: #333;
  text-align: center;
  font-family: "Open Sans", sans-serif;
  bottom: 0;
  height: 100px;
  left: 0;
  z-index: 100;
  display: block;
  float: right;
}
```

### 4.3. CSS Class Names

Use names in lowercase and separate them using dashes.

```css
/* Good */
.page-header {
  ...
}

/* Bad */
.pageHeader {
  ...
}
.page_header {
  ...
}
```

Avoid giving too short names for classes and always choose meaningful names that provide the class function.

```css
/* Good */
.btn { ... }
.page-header { ... }
.progress-bar { ... }

/* Bad */
.b { ... }
.ph { ... }
.block { ... }
```

### 4.4. CSS Performance

Avoid using ID's.

```css
/* Good */
.header { ... }
.section { ... }

/* Bad */
#header { ... }
#section { ... }
```

Do not use selectors standards for not generic rules, always prefer using classes.

```css
/* Good */
.form-control { ... }
.header { ... }
.section { ... }

/* Bad */
input[type="text"] { ... }
header { ... }
section { ... }
```

Nest only when need change the class comportament with interference for other class. Keep the nested on max of three elements.

```css
/* Good */
.modal-footer .btn { ... }
.progress.active .progress-bar { ... }

/* Bad */
.modal-btn { ... }
.progress.active .progress-bar .progress-item span { ... }
```

> **NEVER** use `!important` and keep in mind that if you need to, there's something wrong

Always minify the build CSS code (and save as `.min.css`). You can use task builders or even node for that.

```css
/* Good */
.navbar{...}.nav{...}.nav-item{...}.nav-link{...}

/* Bad */
.nav-item {
  ...
}
.nav-link {
  ...
}
```

### 4.5 CSS Media Queries

Start the development with generic rules with and add media queries with mobile first (always using `min-width` as query condition).

```css
/* Good */
.navbar {
  margin-bottom: 20px;
}

@media (min-width: 480px) {
  .navbar {
    padding: 10px;
  }
}

@media (min-width: 768px) {
  .navbar {
    position: absolute;
    top: 0;
    left: 0;
  }
}

@media (min-width: 992px) {
  .navbar {
    position: fixed;
  }
}

/* Bad */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
}

@media (max-width: 767px) {
  .navbar {
    position: static;
    padding: 10px;
  }
}

```

Keep the media queries as close as possible to their relevant rule sets. Don't bundle them all in a separate stylesheet or at the end of the document.

```css
.navbar { ... }
.nav { ... }
.nav-item { ... }

@media (min-width: 480px) {
  .navbar { ... }
  .nav { ... }
  .nav-item { ... }
}
```

## 5. SASS

## 6. JavaScript

## 7. C++

## 8. References

No one works alone, so I've wrote this document based on:

* [Code Guide by @mdo](https://github.com/mdo/code-guide)
* [Felipe Fialho Coding Style](https://github.com/LFeh/coding-style/)
* [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style/)


## 9. License

This project is licensed under the terms of the [MIT](LICENSE) license.
