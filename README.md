# The Style Elements Library for Elm

> This library is experimental.  Try it out and let me know your feedback!

It's easy to write _valid_ CSS that is still broken and frustrating.  In dealing with CSS we have to handle inconsistent browser defaults, sometimes mysterious parent-child interactions, confusing property naming, and a whole host of unintuitive workarounds.

What if we could just make broken styles not expressible?  It takes a lot of discipline to make a well crafted stylesheet, why can't we shift that discipline to the elm compiler?  We can get a lot farther by having a library that sets smart defaults and protects you from the parts of CSS that bite.

That's the aim of `style-elements` library. To give you the tools to write styles that are intuitive and robust, while still being productive and expressive.  To make styles that don't break.

And while we're at it, it wouldn't hurt to have built in support for `animations`, `transitions`, and `media queries` too, so that we can make our webapp feel modern and responsive.

Maybe styling can actually be _fun_ now.


## Getting Started


 * a simple example: [code]() - [demo]()
 * a realworld example that uses animations, media queries, and palettes: [code]() - [demo]()
 * documentation (Unpublished for the moment, will be published soon)


# High Level View

There are two parts to this library.

## Style Crafting

The `Style` module has the tools you need to craft a style.  Essentially you do this by creating a `Style.Model` record.  

The `Style.Model` is a pretty large record with a handful of required properties. These required properties 

You don't need to write an entire `Style.Model` by hand for every style in your library.  Generally you'll create one foundational style and then all the other styles will be based on that foundation.  This allows us to have very explicit inheritance which makes styling much easier to think about.

There's still one big question though; How do we associate a style with an html node?  Usually you'd do this with a `class` or `id`, but this library does things a bit differently.


## Attaching Styles to Elements

Instead of relying on `classes` and `ids`, the `style-elements` library focuses on creating collections of styled elements that you can pull from and use to build your view.  While this may seem bizarre, the benefit is that your views look cleaner and more meaningful, and we still maintain our ability to express style variations like we would with classes (such as if you're used to using `classList`).


The `Style.Elements` module has the tools to attach a style to an html node.  We call an html node with an attached style a `Style.Element`, and it works very similarly to the nodes from the `Html` library that you're used to.

You can use `Html.Attributes` and `Html.Events` on them as you would.  The only requirement is that the child nodes are `Style.Element`s as well.

If this seems confusing, check out the examples.


### Building a Stylesheet

Once your view is composed of `Style.Element`s, you can call `Style.Elements.build` at the top-most element.  This gathers all the styling information you've specified in the elements of your view and builds a stylesheet.  This stylesheet is then embedded into the html.


> We have to use style sheets because inline styles can't express desireable things like media queries and animations.  However this library doesn't require you to write css classes, so how does a stylesheet associate styles with an html node?
>
> Internally, a classname for a style is generated by taking a murmur3 hash of the style properties.  This classname is also used to eliminate redundant styles when the stylesheet is created.


Options for generating external css stylesheets are currently being considered.


## A Starterkit

The `Style.Basic` module contains useful styles to get you started.

The `Style.Elements.Basic` module contains useful elements to start with.



