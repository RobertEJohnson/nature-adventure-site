# Learning Notes

The goal here is just to write it all down, if I know it or not. More practice, and in the future if it slips my mind I can look back.

## Lecture Lessons


### Creating the header

How to clip parts of the elements using the clip-path property.
- clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%) to make a rectangle

How to set project-wide font definitions.
- Use the body tag and let inheritance do the rest.
  
A good way to perform a basic reset using the universal selector.
- * and margin, padding to 0, and box-sizing: border-box;

THE BEST WAY to perform a basic reset using the universal selector.
- *, *::after, *::before margin and padding to 0 and box-sizing: INHERIT; 
- html {box-sizing: border-box;}
This will ensure to overwrite content-box box-sizing if it is specifically applied in a library, or file you didn't write.

Overlaying multiple background-images, just apply an additional property value.
- background-image: linear-gradient(values), url(url);

Easy ways to specify direction with a linear-gradient using ```to``` and chained directions
- linear-gradient(to left top,rgba(128, 214, 113, .6), rgb(40, 180, 133, .6)))

### Header continued

Easy way to center anything with CSS with transform, top and left properties.
- top, right, bottom, left will all position an element relative to its parent
- transform: translate(-50%, -50%); will shift an element half of its own height and width upwards and leftwards. It is not relative to its parent.

Transform text to uppercase.
- text-transform: uppercase;

Increase the spacing between letters within text.
- letter-spacing: 17px;

### CSS Animations

There are generally two types of animations 

Using Transitions and hover effects.

#### Animated Button

What are pseudo-elements and pseudo-classes?

Ripped from w3schools
The :visited selector is used to select visited links.
Tip: Use the :link selector to style links to unvisited pages, the :hover selector to style links when you mouse over them, and the :active selector to style links when you click on them.

How and why to use the ::after pseudo-element;
- must specify display type and content
- can be used to 


How to create a creative hover animation effect using the transition property.

/* The first 0% keyframe styles will be applied before the animation starts */
```animation-fill-mode: backwards;```

### Three Pillars of HTML / CSS

1. Responsive Design

We build one website that works beautifully between all devices.

- Fluid layouts
- Media queries
- Responsive units
- Correct units
- Desktop-first vs mobile-first

2. Maintainable and Scalable Code

Most important for you the developer.

- Clean
- Easy to understand
- Supports Growth
- Reusable
- How to organize files
- How to name classes
- How to structure HTML

3. Web performance

Making a web app faster and smaller in size, so a user downloads less data.

- Less HTTP requests
- Less code
- Compress code
- Use a CSS preprocessor
- Less images (Only use images that are necessary, images take up most of the size of a site.)
- Compress images

### How CSS Works Behind the Scenes

What happens to css when we load up a webpage?

- The browser loads the initial HTML file
- It parses the HTML
- Builds the Document Object Model
- As the browser parses the HTML it find the css and begins parsing.

Parsing CSS

- First resolve conflicting CSS declarations (cascade)
- Second step is processing final CSS Values
  (50% on a smartphone is completely different than a large screen)

- Final CSS is stored on the CSS Object Model

Render Tree

- Is formed through combination of DOM and CSSOM

Website rendering the ```visual formatting model```

- This algorithm calculates and uses box-model, floats etc.
  Once the visual formatting model is finished we can move on to the final rendered version. The Paint.

### CSS Rules

A CSS Rule consists of a ```selector``` and a ```declaration block```

```.my-class``` is the selector and ```{color: blue;}``` is the declaration block. 

```color``` is a CSS Property and ```blue``` is a declared value.

### CSS Parsing Phase

The first step in the CSS Parsing Phase to resolve conflicting CSS declarations.

This is the process of combining different stylesheets and resolving conflicts between different CSS rules and declarations, when more than one rule applies to a certain element.

CSS can come from different sources.
1.  Author declarations (styles we as a developer write).
2.  User declaration (when a user changes browser text).
3.  Browser (User agent).

#### How does the cascade (parsing first step) actually work?:

Importance > Specificity > Source Order

Importance:
1. User !important declarations
2. Author !important declarations
3. Author declarations
4. User declarations
5. Default browser declarations

Same Importance? Calculate ```Specificity Score```:
1. Inline Styles
2. IDs
3. Classes, pseudo classes, attribute.
4. Elements, pseudo-elements.

Inline / IDs / Classes / Elements
            (0,0,0,0)

```.button {color: white;}```

The specificity score of the above class is (0,0,1,0)

Same Specificty Score? Calculate ```Source Order```
1. (0,1,0,0) vs (0,1,0,0) The ```last``` declaration will override all other declarations and will be applied.

##### Recap

- CSS declarations marked with !important have highest priority when multiple resources are in conflict.
- Only use !important as a last resource.
- Correcting specificities makes ```maintainable code```.
- Inline styles will always have priority over styles in external stylesheets.
- A selector that contains 1 ID is more specific than one with 1000 classes.
- A Universal selector ```*``` has NO specificty value (0,0,0,0);

CSS Ordering Notes:
- ```Rely on specificity``` rather than ```order`` of selectors.
  This way if you ever need to reorder specificity
- ```Rely on order``` when using 3rd party stylesheets, put your ```author stylesheet LAST```.
  This way you overwrite styles that you want to write if they exist.

All of this is ```Cascade```.

**Interesting Note:**
Pseudo classes ARE counted towards specificity score, so its quite possible that the only ```:hover``` effect will not occur even though there are no other ```:hover``` effects if there is a higher specificity score else where.

**This Loses even though it's the only pseudo-class, so it DOESN'T apply**
#nav a.button: hover {
    color: red;
}

**This Wins even though it doesn't have hover, so it applies**
#nav a.button div.pull-right{
    color: blue;
}

### How CSS Values are Processed

Each time we use ```em``` or ```rem``` it will be converted to pixels.

How does this happen?
Knowing this will help predict what value takes the final render.

How CSS is processed:

Part 1: Get the value
1. declared values
   - author declarations
2. cascaded value
   - after the cascade
3. specified value
   - defaulting if there is no cascaded value
   - also defaulting if there is no browser value
   - It is an ```initial value```.

Part 2: Calculate the value
4. computed value
   - converting relative values to absolute
5. used value
   - final calculations, based on layout
6. actual value
   - browser and device restrictions (rounding pixels etc)

font-size is an inherited value!
- Declare font-size on a parent and you're set.
- This avoids having to declare font-size on every element.

```rem`` values are calculated from the default pixel values! 1.5rem will convert to 24px if the default pixel size is 16px.

--

Relative units are fundamental to designing responsive layouts.

Percentages:
- differ from font-sizes to lengths!

Fonts:
150% -> x% * parent's computed font size -> 24px

Lengths:
10% --> x% * parent's computed width --> 100px

Ems vs Rems:
- Ems use the ```parents values```.
- Rems use the ```root elements values```.

Fonts em:
3em --> x * ```parent``` computed font-size --> value

Lengths em:
2em --> x * ```current`` element font-size --> value

Rem:
10rem --> x * root computed font-size --> 160px

vh:
1vh --> 1% of the viewport height

vw:
1vw --> 1% of the viewport width

--

- Each css property has an initial value, regardless of declarations or inheritance.

- Browsers specify a default root font-size for each page, THIS IS NOT an initial value.

- Percentages and relative values are always converted to pixels.

- ```Percentages``` are measured relative to ```their parents font-size``` if used to specify ``font-size``

- ```Percentages``` are measured relative to ```their parents width``` if used to specify ```length```.

- ```em``` are measured relative to their ```parents font-size``` if used to specify ```font-size```;

- ```em``` are measure relative to the ```current font-size``` if used to specify ```lengths```.

- ```rem``` are always measured relative to the ```document's root font-size```

- ```vh and vw``` are simply percentage measurements of the ```viewport's height and width```.

--

Inheritance passes the values for some specific properties from parents to children - more maintainable code;

Rule of thumb, properties related to fonts like font-family, font-size, color are all inherited.

The computed value of a property is what gets inherited, not the declared value.

Inheritance of a property only works if no one delcares a value for that property.

We can use the ```inherit``` keyword to force inheritance on a certain property.

We can use the ```initial``` keyword to reset a property to its initial value.

--

### How and Why to use rem Units

We want an easy way to change all the measurements on the page with one simple setting. 

For example, when we hit a breakpoint for a mobile device.

Instead of writing hundreds of lines of code with media queries we can change simple setting, the global font-size.