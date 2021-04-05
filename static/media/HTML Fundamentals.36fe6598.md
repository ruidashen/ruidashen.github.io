## HTML Fundamentals

### Q: What is semantic HTML?

### A: 

Long before the existence of front end developers, the websites were created and maintained by the back end engineers, they usually layout their website by using tables, for me it is hard to read and difficult to maintain, after, things got improved, there were the DIV + CSS layout, which improved the readablity of the codes, however it is still hard to maintain by other developers. Finally, front end developers showed up, they use the right tags in the right place, and layout using modern techniques, which resulted in better readablity and maintainable codes, also writing semantic HTML shows just how professional you are as a front end developer.

### Q: What does the <meta name="viewport"> tag do?

### A: 
```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1">
```
The viewport settings related to mobile responsiveness, you can set up the width to be device width, which means that it will use the physical width of the device (instead of zooming out) which is good with mobile friendly pages as well as the initial-scale(usually 1).

### Q: What are some HTML5 elements?

### A: Some common HTML5 elements are: 

- content related: ```<header>``` ```<main>``` ```<footer>``` ```<article>```
- utilities: 
  - ```<canvas>``` The Canvas API provides a means for drawing graphics via JavaScript and the HTML ```<canvas>``` element. Among other things, it can be used for animation, game graphics, data visualization, photo manipulation, and real-time video processing (MDN).
  - ```<video>``` The HTML Video element (```<video>```) embeds a media player which supports video playback into the document. You can use ```<video>``` for audio content as well, but the ```<audio>``` element may provide a more appropriate user experience (MDN).
  - ```<audio>``` The HTML ```<audio>``` element is used to embed sound content in documents. It may contain one or more audio sources, represented using the src attribute or the ```<source>``` element: the browser will choose the most suitable one. It can also be the destination for streamed media, using a MediaStream (MDN).