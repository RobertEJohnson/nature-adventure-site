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

