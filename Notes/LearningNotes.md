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