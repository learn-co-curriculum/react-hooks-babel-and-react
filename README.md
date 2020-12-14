# Babel and React

## Overview

In this lesson, we'll unpack what **Babel** brings to the table when developing React applications.

## Objectives

1. Learn what Babel is
2. Learn how Babel integrates with React
3. Frame Babel's relative importance at this stage in learning React

# Babel

![Tower of Babel](http://www.ancient-origins.net/sites/default/files/field/image/tower-of-babel-2.jpg)

If you don't have time to procrastinate and [read the wiki][origin-myth], and
want to get on with learning programming, allow us to provide the
[TL;DR][tl;dr] and why it is relevant to the Babel tool we use:

The Tower of Babel was a colossal construction project long ago. It was being
built by a united humanity speaking the same language, with the intention of
reaching such heights that heaven itself could be accessed. While it was being
constructed, the God in the story, (for debated reasons), afflicted the united
humans by confounding their speech. This ensured the once united humanity could
no longer communicate. What made this ambitious project possible was that
multiple cultures, languages, idioms, etc. were all using _a common standard_.

As you may already know, JavaScript (based on the ECMAScript [ES] standard) is
an evolving language. Over time we have had several iterations. For the most
part, ECMAScript's evolution has changed to incorporate more features and
language constructs over time (think ES6 arrow functions, class syntax, `let`,
and `const` vs. their absence in ES5!). This resembled the "confounded" state
described above. What was needed was a way to move all, various standards of
JavaScript usage to the same standard. **That** is what the Babel program does
&mdash; it makes all JavaScript versions emit a common, standard code.

Less metaphorically, Babel gained popularity because it
[compiled/transpiled][transpile-compile] newer ES6 syntax and language features
into the older (and more widely deployed, at that time) ES5. This was especially
important when ES6 came out because many browsers had not yet updated their
JavaScript engines to interpret the new language features of ES6.

Nowadays, you are less likely to encounter browsers **not** implementing ES6
syntax. JavaScript is still updated regularly, and most modern browsers do a
good job keeping up! If you're ever curious about whether or not a particular
feature is supported in a browser, [caniuse.com][] is a great resource.

#### Then why is Babel important?

If most popular browsers have moved to integrate ES6+ syntax, then why is Babel
"still a thing?"

Babel's competency was in reading in one type of text and making in-place
transformations such that another type of text came out. Some developers
realized that by processing their code with Babel, they could write
code that's terse and convenient and then have Babel turn that code into
verbose, compliant JavaScript code.

Let's take as an example how non-standard JSX (JSX is a React specific syntax)
can be transformed, via Babel, into compliant JavaScript. Succinctly, **Babel
turns JSX into normal JavaScript written with the React library**:

```js
const profile = (
  <div>
    <img src="avatar.png" className="profile" />
    <h3>{[user.firstName, user.lastName].join(" ")}</h3>
  </div>
);
```

...when the above is run through Babel, we receive the following executable code:

```js
var profile = React.createElement(
  "div",
  null,
  React.createElement("img", { src: "avatar.png", className: "profile" }),
  React.createElement("h3", null, [user.firstName, user.lastName].join(" "))
);
```

Don't worry if the syntax above is unfamiliar! The sentiment you want to take
away is that JSX code in the first block (that _HTML-like_ syntax) was transformed
into valid JavaScript syntax in the second block after Babel had a go at it.

While you don't **strictly** need Babel as a dependency when writing React code,
there aren't many (if any) developers who write React applications without JSX
(and therefore Babel). My fingers think that typing that first one is better
(because they're lazy). My brain also likes that JSX paints an HTML picture in
my mind's eye. JSX removes the burden on the programmer to calculate an
intermediary picture of the DOM in their brain when reading this code. So, we
teach and write using the pre-Babel-compiled (first syntax above) JSX in our
React applications.

#### Not Just For JSX

In addition to the JSX magic it provides, Babel can also compile other features
and syntactic sugar that is not yet, or never will be, a part of ECMAScript! One
example of this is a Babel plugin that enables the usage of
[language features proposed for ECMAScript, but not yet implemented][babel-stage-2].

## Summary

You have just been introduced to a tool you likely have not worked directly with
before. Luckily, it's straightforward to summarize:

**Babel** enables us to use syntax that browsers won't natively recognize by
**pre-compiling** (or _transpiling_) it into syntax that browsers _do_ natively
recognize. When used with React, this can (and in our case will) include, but
not be limited to, transpiling JSX.

## Looking Forward

That was a chunk of new information, and we have even more coming up. If this is
your first time being exposed to a tool like Babel, treat yourself. Stand up,
stretch your legs, look at a real human that's not in meme format: you deserve
it. When you come back, we will get started on **Webpack** in the following
lesson.

## Resources

- [Babel][babel]

<p class='util--hide'>View <a href='https://learn.co/lessons/babel-and-react'>Babel and React</a> on Learn.co and start learning to code for free.</p>

[origin-myth]: https://en.wikipedia.org/wiki/Tower_of_Babel
[tl;dr]: https://en.wikipedia.org/wiki/TL;DR
[babel]: http://babeljs.io/
[transpile-compile]: https://stackoverflow.com/questions/43968748/is-babel-a-compiler-or-transpiler
[caniuse.com]: https://caniuse.com/
[babel-stage-2]: https://babeljs.io/docs/plugins/preset-stage-2/
