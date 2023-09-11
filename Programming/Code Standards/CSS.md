# CSS

## Prefer Classes to IDs

You should still use IDs for JavaScript targeting, but they’re not required for CSS because they’re too specific. If one object uses an ID for CSS styling it can never be replicated since IDs are unique identifiers. If you use classes for styling then inheritance becomes much easier to predict.

Moreover, classes can be chained together for extra features. A single element could have 10+ classes attached to it. While 10+ classes on one element isn’t something I’d personally recommend, it does allow developers to amass a library of reusable styles for unlimited page elements.

## Class Naming

Keep classes short and to the point. use all lowercase and no hyphens. Many third party libraries like bootstrap use this convention, so we'd like to do the same for consistency.

When shortening words, be consistent and consider using the full word instead. I do use some things like **nav-bar-title** instead of **navigation-bar-title** because this is a standard naming convention among many third party libraries, but I also avoid things like **item-num** in favor of **item-number**. The most important thing is to be consistent. If you shorten number to num, be sure to use that convention throughout your style sheet.

## Formatting

Use 4 space tabs for indenting. Open and close braces should both be on there own line and line up with the rules it applies to.

### Example

```css
.class-name-1,
.class-name-2,
p.class-3
{
    /* Even if there's only one line */
}
```

## Avoid Descendant Class Specificity

This only means that you should avoid using child selectors whenever possible. When customizing any unique page elements like anchor links, headers, blockquotes, or unordered lists, you should give them unique classes rather than descendant selectors.

Here’s a simple example:

### Less Specific

```css
.sidebar
{
    /* sidebar contents */
}


h2.sidebar-title
{
    /* The h2 used like this does not add to specificity.
   This is not the same as h2 .sidebar (with a space) 
   which makes the class a child selector and would
   probably not work as intended.*/
}
```

### More Specific

```css
.sidebar
{
    /* same sidebar contents */ 
}

.sidebar h2
{
    /* The fact that the h2 is a descendent of the
    .sidebar increases specificity. */
}
```

Although it’s not horrendous to use the second code format, the first is recommended to keep specificity low for the sake of inheritance.

## Repeatable Classes

Define unique styles with repeatable classes (floats, clearfix, unique font stacks).

## Use flexible/relative units

For maximum flexibility over the widest possible range of devices, it is a good idea to size containers, padding, etc. using relative units like ems and rems or percentages and viewport units if you want them to vary depending on viewport width.

If you don't understand the various units, **rem** is pretty save overall. It's based on the root elements font size.

Here's an [MDN Page](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units#relative_length_units) outlining the differences between the many, many units available.

## !important

!important is a last resort. Use it only when you need to override something and there is no other way to do it; things like third party overrides. Even here, be careful. The only way to override these rules is with another, more specific !important rule or an inline style. It get's ugly really fast.

**Using !important is a bad practice and you should avoid it wherever possible.** If this is showing up frequently in your rules, get some help. There is likely something fundamentally wrong with your approach.

## Media Queries

### Responsive Designs

To begin with, media queries are less necessary now than in years past. There are several new tools in modern CSS that allow fluid layouts and responsive text that don't require any media queries at all. The advantage is that you don't need to design for every potential screen width.

Consider learning the ins and outs of **display: flex** and **display: grid**, as well the functions **calc()** and **clamp()**. There's more, but these are the ones I find the most useful.

These four features have very wide browser support, greatly simplify your code, and make things much easier to maintain. You will still need media queries, but these tools make the media queries you do write far more flexible.

### Mobile-first media queries

Your styles should first target narrow screen/mobile styling before any other media queries are encountered. Add styling for wider viewport sizes via successive media queries. Following this rule has many advantages that are explained in this [Mobile First article](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design).

```css
/* Default CSS layout for narrow screens */

@media (min-width: 480px)
{
  /* CSS for medium width screens */
}

@media (min-width: 800px)
{
  /* CSS for wide screens */
}

@media (min-width: 1100px)
{
  /* CSS for really wide screens */
}
```

### Placement of Queries

Put the relevant media queries near the original rules. This does result in duplicated code, but it's much easier to maintain.

## Organization

Once you get a significant number of rules organize them with headers and a table of contents. Here's a sample based on WordPress, twenty-twenty-one theme. It's a pretty good base to start with. Just delete or add whatever seems appropriate.

```css
/**
 * VARIABLES
 * Font Family 
 * Font Size 
 * Colors 
 * Header 
 * Main navigation 
 * Pagination 
 * Footer 
 *
 * SETTINGS
 * File-header..........The file header for the themes style.css file.
 * Fonts................Any font files, if the project needs specific fonts.
 * Global...............Project-specific, globally available variables.
 *
 * TOOLS
 * Functions............Global functions.
 * Mixins...............Global mixins.
 *
 * GENERIC
 * Normalize.css........Normalise browser defaults.
 * Breakpoints..........Mixins and variables for responsive styles
 * Vertical-margins.....Vertical spacing for the main components.
 * Reset................Reset specific elements to make them easier to style in other contexts.
 * Clearings............Clearings for the main components.
 *
 * ELEMENTS
 * Blockquote...........Default blockquote.
 * Forms................Element-level form styling.
 * Headings.............H1–H6
 * Links................Default links.
 * Lists................Default lists.
 * Media................Images, Figure, Figcaption, Embed, iFrame, Objects, Video.
 *
 * BLOCKS
 * Audio................Specific styles for the audio block.
 * Button...............Specific styles for the button block.
 * Code.................Specific styles for the code block.
 * Columns..............Specific styles for the columns block.
 * Cover................Specific styles for the cover block.
 * File.................Specific styles for the file block.
 * Gallery..............Specific styles for the gallery block.
 * Group................Specific styles for the group block.
 * Heading..............Specific styles for the heading block.
 * Image................Specific styles for the image block.
 * Latest comments......Specific styles for the latest comments block.
 * Latest posts.........Specific styles for the latest posts block.
 * Legacy...............Specific styles for the legacy gallery.
 * List.................Specific styles for the list block.
 * Media text...........Specific styles for the media and text block.
 * Navigation...........Specific styles for the navigation block.
 * Paragraph............Specific styles for the paragraph block.
 * Pullquote............Specific styles for the pullquote block.
 * Quote................Specific styles for the quote block.
 * Search...............Specific styles for the search block.
 * Separator............Specific styles for the separator block.
 * Table................Specific styles for the table block.
 * Verse................Specific styles for the verse block.
 * Video................Specific styles for the video block.
 * Utilities............Block alignments.
 *
 * COMPONENTS
 * Header...............Header styles.
 * Footer...............Footer styles.
 * Comments.............Comment styles.
 * Archives.............Archive styles.
 * 404..................404 styles.
 * Search...............Search styles.
 * Navigation...........Navigation styles.
 * Footer Navigation....Footer Navigation styles.
 * Pagination...........Pagination styles.
 * Single...............Single page and post styles.
 * Posts and pages......Misc, sticky post styles.
 * Entry................Entry, author biography.
 * Widget...............Widget styles.
 * Editor...............Editor styles.
 *
 * UTILITIES
 * A11y.................Screen reader text, prefers reduced motion etc.
 * Color Palette........Classes for the color palette colors.
 * Editor Font Sizes....Editor Font Sizes.
 * Measure..............The width of a line of text, in characters.
 */

/* Categories 01 to 03 are the basics. */

/*******************
/**** VARIABLES ****
********************/
:root {

/* Font Family */

/* Font Size */

/* Colors */

/* Header */

/* Main navigation */

/* Pagination */

/* Footer */
}

/********************
/**** COMPONENTS ****
*********************/

/* Header */

/* Footer */
```