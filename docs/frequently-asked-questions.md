---
description: Get answers to common questions about Atomizer. 
layout: docs
section: docs
title: Frequently Asked Questions
---

This section is intended to answer common questions related to Atomic CSS and Atomizer. If you&#39;re unable to find an answer to your question, [you can find support here](/support.html) or [start a discussion here](https://github.com/acss-io/atomizer/discussions).

## Atomic CSS architecture

### What is Atomic CSS?

Atomic CSS is a collection of single purpose styling units (_single responsibility principle for maximum reuse_) that fits well with components in templated frameworks such as [React](https://github.com/facebook/react), [Ember](https://github.com/emberjs/ember.js/), or [Angular](https://github.com/angular/angular.js).

Atomic classes and their associated styling are **immutable**, meaning you&#39;d use the same classes whatever the project you&#39;re working on or the team you&#39;re working with. In other words, Atomic CSS is a common &quot;vocabulary&quot; meant to style documents _regardless of context or content_.

For more information about Atomic CSS, we recommend that you read [Challenging CSS best practices](http://www.smashingmagazine.com/2013/10/21/challenging-css-best-practices-atomic-approach/) on Smashing Magazine, watch the [Atomic CSS presentation](https://www.youtube.com/watch?v=ojj_-6Xiud4) on youtube, or check the [Atomic CSS slide deck](https://www.haikudeck.com/atomic-css-uncategorized-presentation-dJ0xlFjhBQ) on haikudeck.

<p class="noteBox info">Note that the above materials are relatively &quot;old&quot; and some of their content may have changed.</p>

### How is Atomic CSS different than using inline styles?

<dl class="dl-list">
    <dt>Inline styling, the bad parts:</dt>
    <dd>High specificity, verbosity, the inability to deal with pseudo-classes or pseudo-elements, and the fact that those bytes are not cached</dd>
    <dt>Inline styling, the good parts:</dt>
    <dd>Scope is limited to the element onto which the classes are  applied to and the styling is *portable* because that styling is *not* contextual.</dd>
</dl>

<img class="Va(m) Pos(r) Mt(30px)" alt="Venn diagram showing the difference between Atomic CSS and inline styling" height="400" src="https://s.yimg.com/os/acss/images/atomic-vs-style.207423c1.gif" />

<table cellspacing="0" class="W(100%) Ta(start)">
    <caption class="Hidden">The difference between inline styling and Atomic CSS</caption>
    <thead>
      <tr>
          <th scope="col" class="P(10px)"></th>
          <th scope="col" class="P(10px) Whs(nw)">Inline styling</th>
          <th scope="col" class="P(10px)">Atomic CSS</th>
      </tr>
    </thead>
    <tbody>
        <tr class="BdT">
            <th scope="row" class="Va(t) P(10px)">Specificity</th>
            <td class="Va(t) P(10px)">1.0.0.0</td>
            <td class="Va(t) P(10px)">0.0.1.0 <a href="#footnote">[1]</a><a id="footnote-1" class="D(ib)"></a></td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Va(t) P(10px)">Verbosity</th>
            <td class="Va(t) P(10px)">High</td>
            <td class="Va(t) P(10px)">Minimal</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Va(t) P(10px)">Abstraction</th>
            <td class="Va(t) P(10px)">None</td>
            <td class="Va(t) P(10px)">Fallbacks, tweaks, LTR/RTL support, etc.</td>
        </tr>
    </tbody>
</table>

### What are the benefits of Atomic CSS?

The main benefit of Atomic CSS is that it prevents bloat by _dramatically reducing redundancy_. This is possible because rules are content agnostic which makes them much more re-usable than rules based on &quot;semantic&quot; selectors (names that relate to _what_ is styled).

It also:

<dl class="dl-list">
    <dt>moves specificity out of the way:</dt>
    <dd>authors do not have to sandbox their styling via contextual selectors, everything is done via generic classes through markup - which normalizes selector *weight* and reduces *scope*.</dd>
    <dt>improves performance:</dt>
    <dd>less bloat means less bytes (*much less*).</dd>
    <dt>removes dependencies:</dt>
    <dd>&quot;components&quot; (or &quot;objects&quot;) *rely on generic CSS rules*, so there is no need to associate them with their own style block or styles sheet.</dd>
    <dt>allows to share content and assets easily:</dt>
    <dd>UI patterns can be easily shared across projects as their styling relies on the same generic set of rules (the same style sheet).</dd>
    <dt>leverages cache:</dt>
    <dd>The style sheet can be cached for a much longer time because authors re-use existing rules rather than adding new ones to the style sheet.</dd>
    <dt>facilitates RTL/LTR interface switch:</dt>
    <dd>Directions (left/right) are abstracted which allows authors to style without much concern for script direction.</dd>
</dl>

This speaks for itself:

```css
.headline,
.cta-button,
.icon-large,
.title,
.intro {
    font-size: 18px;
}
```

versus:

```css
.Fz(large) {
    font-size: 18px;
}
```

<p class="noteBox info">For the sake of readability, CSS classes on this page *do not* include the escape character (`\`) where it should be needed.</p>

Such approach produces less of everything:

<table cellspacing="0" class="W(100%) Ta(c)">
    <caption class="Hidden">Table comparing yahoo.com against other web sites</caption>
    <thead>
      <tr class="Bgc-#ececec">
          <th scope="col" class="P(10px)"></th>
          <th scope="col" class="P(10px) Whs(nw)">rules</th>
          <th scope="col" class="P(10px)">selectors</th>
          <th scope="col" class="P(10px)">declarations</th>
          <th scope="col" class="P(10px)">properties</th>
          <th scope="col" class="P(10px)">font-size</th>
          <th scope="col" class="P(10px)"><abbr title="Kilobyte">KB</abbr></th>
      </tr>
    </thead>
    <tbody>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">twitter.com</th>
            <td class="P(10px)">6,372 <a href="#footnote">[2]</a><a id="footnote-2" class="D(ib)"></a></td>
            <td class="P(10px)">9,104</td>
            <td class="P(10px)">15,000</td>
            <td class="P(10px)">135</td>
            <td class="P(10px)">755</td>
            <td class="P(10px)">585</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">facebook.com</th>
            <td class="P(10px)">3,316</td>
            <td class="P(10px)">4,018</td>
            <td class="P(10px)">7,947</td>
            <td class="P(10px)">103</td>
            <td class="P(10px)">157</td>
            <td class="P(10px)">281</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">medium.com</th>
            <td class="P(10px)">3,090</td>
            <td class="P(10px)">4,030</td>
            <td class="P(10px)">7,321</td>
            <td class="P(10px)">150</td>
            <td class="P(10px)">432</td>
            <td class="P(10px)">282</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">youtube.com</th>
            <td class="P(10px)">3,530</td>
            <td class="P(10px)">4,684</td>
            <td class="P(10px)">9,005</td>
            <td class="P(10px)">136</td>
            <td class="P(10px)">336</td>
            <td class="P(10px)">352</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">tumblr.com</th>
            <td class="P(10px)">5,647 <a href="#footnote">[2]</a><a id="footnote-2b" class="D(ib)"></a></td>
            <td class="P(10px)">7,616</td>
            <td class="P(10px)">18,100</td>
            <td class="P(10px)">253</td>
            <td class="P(10px)">499</td>
            <td class="P(10px)">733</td>
        </tr>
        <tr class="BdT Bgc-#ff0">
            <th scope="row" class="Ta(start) P(10px)">yahoo.com</th>
            <td class="P(10px) Fw(b)">1,891</td>
            <td class="P(10px) Fw(b)">2,311</td>
            <td class="P(10px) Fw(b)">4,579</td>
            <td class="P(10px) Fw(b)">124</td>
            <td class="P(10px) Fw(b)">71</td>
            <td class="P(10px) Fw(b)">189</td>
        </tr>
    </tbody>
    <tfoot>
      <tr class="Bgc-#ececec">
          <th scope="col" class="P(10px)"></th>
          <th scope="col" class="P(10px) Whs(nw)">rules</th>
          <th scope="col" class="P(10px)">selectors</th>
          <th scope="col" class="P(10px)">declarations</th>
          <th scope="col" class="P(10px)">properties</th>
          <th scope="col" class="P(10px)">font-size</th>
          <th scope="col" class="P(10px)"><abbr title="Kilobyte">KB</abbr></th>
      </tr>
    </tfoot>
</table>

<small>Source: <a href="http://cssstats.com">cssstats.com</a></small>

The table above uses yahoo.com for reference as this site used&mdash;at the time this was published&mdash;a static Atomic CSS library.

### Should I &quot;atomize&quot; everything? Should I style everything using atomic classes?

If changing some styling requires you to edit multiple files, then you should use the classic CSS approach: apply a &quot;meaningful&quot; class to the element you want to style and use that hook to write rules in a style sheet. But if changing a given style across the board can be done in one place&mdash;other than a style sheet&mdash;then you should go with Atomic CSS.

An example of the former could be headings (unless they are &quot;components&quot;) meant to look the same across many modules, or any other styling meant to be shared across different modules. An example of the latter is a component that lives in a template or a JS file, like a specific widget with its own styling.

### I have always been told to use classes related to content, _not to presentation_. Isn&#39;t Atomic CSS promoting bad practice?

<blockquote>
    <div>
        <p class="Mt(0)">
        Despite the <a href="http://dev.w3.org/html5/spec/global-attributes.html#classes">HTML5 specification section on classes</a> repeating the assumed “best practice” that…</p>
        
        <blockquote>
            <div>
                …authors are encouraged to use [class attribute] values that describe the nature of the content, rather than values that describe the desired presentation of the content.
            </div>
        </blockquote>
        …there is no inherent reason to do this. In fact, it’s often a hindrance when working on large websites or applications.
    <small><a href="http://nicolasgallagher.com/about-html-semantics-front-end-architecture/">About HTML semantics and front-end architecture</a></small>
    </div>
</blockquote>

The sole purpose of classes is to provide hooks for styling and behavior. They are not exposed to end users, nor parsed by screen-readers or search engines [[3]](#footnote).

The main goal of Atomic CSS is to reduce bloat, so to better achieve this we must ignore content and context as much as possible.

Look at the following snippet for example (a carousel without a `carousel` class). It creates a working carousel. We put things together in the markup, there is no need for &quot;carousel&quot; rules in the style sheet. If we wanted to show only 2 items per view, we would simply replace W(20%) with W(50%) - that’s it.

```html
<div data-plugin="carousel">
    <div class="Ov(h) Pos(r)">
        <ul class="M(0) P(0) Whs(nw)">
            <li class="D(ib) W(20%)">...</li><!--
         --><li class="D(ib) W(20%)">...</li><!--
         --><li class="D(ib) W(20%)">...</li><!--
         --><li class="D(ib) W(20%)">...</li><!--
            ...
        --></ul>
    </div>
</div>
```

Unlike a `.carousel` class, all the above classes can be re-used to style any other widget.

### Isn&#39;t Atomic CSS moving bloat from style sheets to HTML?

The table below represents the average number of characters per class attribute on a page. Note that Facebook appears to uglify some classes.

<table cellspacing="0" class="Ta(c)">
    <caption class="Hidden">Number of characters per class attributes between web sites</caption>
    <thead>
      <tr>
          <th scope="col" class="P(10px)"></th>
          <th scope="col" class="P(10px) Whs(nw)">Number of characters per `@class`</th>
      </tr>
    </thead>
    <tbody>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">twitter.com</th>
            <td class="P(10px)">28</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">facebook.com</th>
            <td class="P(10px)">17 <a href="#footnote">[4]</a><a id="footnote-4" class="D(ib)"></a></td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">usatoday.com</th>
            <td class="Va(t) P(10px)">38</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) Va(t) P(10px)">theguardian.com</th>
            <td class="P(10px)">36</td>
        </tr>
        <tr class="BdT">
            <th scope="row" class="Ta(start) P(10px)">yahoo.com</th>
            <td class="P(10px) Fw(b)">22</td>
        </tr>
    </tbody>
</table>

The table above uses yahoo.com for reference as this site uses an early version of Atomic CSS.

<h4 id="gzip-loves-atomic-css">Gzip loves Atomic CSS</h4>

If we put Gzip into the picture, then things look even better. That’s because a lot of repetitions means a better compression ratio. From a few tests we ran, it’s about 35% for semantic classes versus 48% for atomic classes.

### How can you distribute presentation changes without asking everyone to change their markup?

Use atomic classes where it makes sense; for example the following creates much of the content of our <a href="./reference">reference</a> page. If we decided to change the styling of this content this would be the only place we&#39;d need to go to.

```jsx
return (
    <div key={'id-' + recipe.id} className={displayclassDefinitions}>
        <h3 className="M(0) Mt(10px) P(10px)">{recipe.name}</h3>
        <dl className="M(0) P(10px) Pt(0) Pend(50px)--sm Ff(m)">{classDefinitions}</dl>
    </div>
);
```

### How does Atomic CSS work with <abbr title="Responsive Web Design">RWD</abbr>?

Please visit our <a href="tutorials/responsive-web-design.html">RWD docs</a> to see examples of how you can use <b class="Fw(b)">Atomizer</b> to create styles in the context of breakpoints.

## Answers related to Atomizer

### How does <b class="Fw(b)">Atomizer</b> compare to Bootstrap, PureCSS, or other CSS framework?

<b class="Fw(b)">Atomizer</b> is not a framework; it does not contain UI components nor a grid system. It is a solution that allows you to to create **your own UI** while preventing bloat.

<b class="Fw(b)">Atomizer</b>&#39;s &quot;footprint&quot; is limited to what a project uses - meaning there is no &quot;entry cost&quot;. Simply installing <a href="/guides/atomizer.html">Atomizer</a> in your project does not add any bytes to your pages.

### Do I need to specify a namespace? And if yes, what should I use?

You do not need to use a namespace per se but this is extremely useful to bump the specificity of Atomic rules. Our advice is to use an `id` (we use `#atomic`) so all Atomic rules can easily overwrite declarations from other rules; for example:

```css
.hero-module .button {
    font-size: 1.6em;
    font-weight: bold;
}
...
#atomic .Fw(n) {
    font-weight: normal;
}
```

```html
<div class="hero-module">
    <button class="button Fw(n)">...</button>
</div>
```

The value for `font-weight` in the `.hero-module .button {...}` rule is overwritten by the Atomic class in the markup <a href="#footnote">[5]</a><a id="footnote-5" class="D(ib)"></a>.

<div class="noteBox info My-1em">
    We like to deal with 5 &quot;specificity&quot; brackets:

    <ul class="ul-list">
        <li>rules involving only type selectors</li>
        <li>rules involving only classes</li>
        <li>rules involving an `id`</li>
        <li>styles set via JavaScript</li>
        <li>rules using `!important`</li>
    </ul>

    This clear separation helps to better manage styles inside large scale projects.

</div>

### Why are Atomizer classes capitalized? As far as I know, no other framework does that?

We took advantage of the fact that nobody seems to capitalize classes and that CSS is case sensitive to get a &quot;cheap&quot; namespace, one that does not rely on extra character(s).

### Why do I have to use lowercase for color values?

To prevent redundancy, we made the choice to favor lowercase over uppercase, even though the latter is valid.

This is because hex classes such as `#fff` and `#FFF` would not duplicate the declaration, but would add an unnecessary selector to the style sheet.

### Why are &quot;descendant classes&quot; not relying on the namespace? Why are those styles using `!important`?

If you have chosen to use a namespace then all Atomic rules rely on that namespace except the ones containing descendant selectors as those are **not** &quot;sandboxed&quot; via that said namespace. Instead, Atomizer adds !important to those styles.

The reason for this is because including the namespace in the selector could make the rule fail to target the node. For example this would not work (using `atomic` as the namespace):

```html
<html id="atomic" class="open">
    ...
    <div class="open_D(b)">...</div>
</html>
```

This is because including the namespace would create the following rule:

```css
#atomic .open .open_D(b) {
    display: block;
}
```

but since `open` is not a descendant of `atomic`, but its sibling, the selector does not target the node thus the style would not apply.

To prevent this issue we have chosen to add `!important` to contextual classes rather than using the namespace. Hence the rule is written like so:

```css
.open .open(Db) {
    display: block !important;
}
```

<p class="noteBox warning">Keep this in mind in case you need to style that same node with JavaScript.</p>

<p class="noteBox info">This is not relevant when there is no namespace set up. In that case, the rule is not written using `!important`.</p>

### How can one remember Atomizer class names?

The syntax comes from <a href="http://emmet.io">Emmet</a>, which is a plugin for many IDEs. It allows you to type a few characters and get property/value pairs. Like Emmet shortcuts, <b class="Fw(b)">Atomizer</b> classes are for the most part simple abbreviations.

Also, note that we do not use `left` and `right` but instead `start` and `end`. So we can easily output a RTL style sheet.

The <a href="../guides/syntax.html">syntax</a> and <a href="reference">reference</a> pages are meant to help you with this; and we may have a plugin for your IDE in the near future...

### How come Atomizer is not creating some classes for me?

Make sure you scan all the files onto which <b class="Fw(b)">Atomizer</b> classes are applied. Using Grunt for example, see **&lt;path to files to be scanned&gt;** below:

```js
module.exports = function (grunt) {
    grunt.config.set('atomizer', {
        dev: {
            options: {
                configFile: './configs/atomizer.json',
                configOutput: './configs/atomizer.json',
                namespace: '#Stencil'
            },
            files: [{
                src: ['components/**/*.jsx'],
                dest: 'build/css/atomic.css'
            }]
        },
        dist: {
            options: {
                configFile: './configs/atomizer.json',
                configOutput: './configs/atomizer.json',
                namespace: '#atomic'
            },
            files: [{
                src: ['<path to files to be scanned>'],
                dest: 'build/css/atomic.css'
            }]
        }
    });

    grunt.loadNpmTasks('grunt-atomizer');
};
```

### How come Atomizer does not add vendor prefixes where needed?

We didn&#39;t want to reinvent the wheel as there are tools out there that do this very well (i.e. <a href="https://github.com/postcss/autoprefixer">autoprefixer</a> (<a href="https://goonlinetools.com/autoprefixer/">available as an online tool</a>)).

---

1. Specificity of Atomic rules can be increased via namespace. You&#39;d use a `type` selector for `0.0.1.1`, a `class` for `0.0.2.0`, and an `id` for `0.1.1.0` <a href="#footnote-1">[↩]</a>.
1. Maximum number of rules for IE9: 4,095 (65,534 for IE10+) <a href="#footnote-2">[↩]</a><a href="#footnote-2b">[↩]</a>.
1. <a href="http://microformats.org/">microformats</a> is a different story <a href="#footnote-3">[↩]</a>.
1. Thanks to some uglification <a href="#footnote-4">[↩]</a>.
1. Choosing a `id` for the namespace (i.e. `#atomic`) guarantees that <b class="Fw(b)">ACSS</b> styles overwrite any other rule in a project based on classes &mdash; regardless how many classes are being used. <br> We do not use `!important` as such styling would overwrite inline styles as well as other rules in a project that could be using an `id` to create more specific styling <a href="#footnote-5">[↩]</a>.
