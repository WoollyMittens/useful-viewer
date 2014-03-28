# useful.viewer.js: Tile Based Image Viewer

This tile-based image viewer loads only the parts of the image that are visible. Not unlike how Google Maps loads map tiles. This demo comes with a web service to divide large images into tiles using PHP, but the concept is easily replicated in other languages.

Try the <a href="http://www.woollymittens.nl/useful/default.php?url=useful-viewer">demo</a>.

## How to include the script

The stylesheet is best included in the header of the document.

```html
<link rel="stylesheet" href="./css/useful-viewer.css"/>
```

This include can be added to the header or placed inline before the script is invoked.

```html
<script src="./js/useful-viewer.js"></script>
```

To enable the use of HTML5 tags in Internet Explorer 8 and lower, include *html5.js*.

```html
<!--[if lte IE 9]>
	<script src="//html5shiv.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->
```

## How to start the script

This is the safest way of starting the script, but allows for only one target element at a time.

```javascript
var viewer = new useful.Viewer( document.getElementById('id'), {
	'urlprefix' : '../',
	'imageslice' : './php/imageslice.php?src={src}&left={left}&top={top}&right={right}&bottom={bottom}&width={width}&height={height}',
	'width' : '100',
	'widthUnit' : '%',
	'height' : '512',
	'heightUnit' : 'px',
	'divide' : '80%',
	'margin' : '0%',
	'colorPassive' : '#ff6a00',
	'colorActive' : '#d45800',
	'colorHover' : '#ff9800',
	'colorDisabled' : '#7f7f7f',
	'lens' : '0.5',
	'toolbars' : 'buttons', 	// buttons | toolbar | sliders | none
	'zoom' : 'static', 			// static | lens
	'spin' : 'slideshow', 		// rotation | slideshow | catalogue
	'pan' : 'drag', 			// drag | hover
	'magnification' : '1.1',
	'max' : '4',
	'grid' : '256px',
	'cache' : '32'
});
```

**id : {string}** - The ID attribute of an element somewhere in the document.

**links : {string}** - A CSS Rule that describes the toggle buttons within *parent*.

**imageslice : {string}** - A web-service for requesting cropped tiles of an image on the server. An example is provided as *./php/imageslice.php*.

**width : {integer}** - The width of the slideshow.

**widthUnit : {string}**
+ *px* - The width would be applied in pixels.
+ *%* - The width would be applied as a percentage of the available space.
+ *em* - The width would be applied relative to the text size.

**height : {integer}** - The height of the slideshow.

**heightUnit : {string}**
+ *px* - The height would be applied in pixels.
+ *%* - The height would be applied as a percentage of the available space. The parent element needs to have a defined height.
+ *em* - The height would be applied relative to the text size.

**divide : {string}** - The percentage of the height devoted to the slides. The rest is reserved for the thumbnails.

**margin : {string}** - The space separating the slides and the thumbnails.

**colorPassive : {color}** - A color name, hex or rgba value  used for the passive state of the buttons.

**colorActive : {color}** - A color name, hex or rgba value  used for the active state of the buttons.

**colorHover : {color}** - A color name, hex or rgba value  used for the hover state of the buttons.

**colorDisabled : {color}** - A color name, hex or rgba value  used for the disabled state of the buttons.

**lens : {float}** - The radius of the lens overlay as a fraction of the width of the viewer.

**toolbars : {string}**
+ *buttons* - Show a minimal set of buttons.
+ *toolbar* - Show a toolbar instead of separate buttons.
+ *sliders* - Use sliders to control the zoom and rotation.

**zoom : {string}**
+ *static* - The main image zooms in.
+ *lens* - A separate lens overlays a zoomed in view.

**spin : {string}**
+ *rotation* - The left/right controls assume the images form a 360 degree rotation of a subject in separate frames.
+ *slideshow* - The left/right controls cycle through slides.
+ *catalogue* - The left/right controls emulate turning a page.

**pan : {string}**
+ *drag* - Adjust the view by dragging the mouse or touch.
+ *hover* - Adjust the view by hovering the mouse.

**magnification : {float}** - The factor by which the magnification increases.

**max : {float}** - The maximum magnification factor.

**grid : {string}** - The size of the tiles that make up the zoomed image.

**cache : {integer}** - How many tiles to keep track of at a time. More slows down the display, but reduces downloads.

## How to control the script

### Focus

```javascript
viewer.focus(index);
```

Highlights and centres a specific thumbnail.

**index : {integer}** - The index of the slide to show.

### Previous

```javascript
viewer.previous();
```

Shows the previous slide.

### Next

```javascript
viewer.next();
```

Shows the next slide

## How to build the script

This project uses node.js from http://nodejs.org/

This project uses grunt.js from http://gruntjs.com/

The following commands are available for development:
+ `npm install` - Installs the prerequisites.
+ `grunt import` - Re-imports libraries from supporting projects to `./src/libs/` if available under the same folder tree.
+ `grunt dev` - Builds the project for development purposes.
+ `grunt prod` - Builds the project for deployment purposes.
+ `grunt watch` - Continuously recompiles updated files during development sessions.
+ `grunt serve` - Serves the project on a temporary web server at http://localhost:8000/ .

## License

This work is licensed under a Creative Commons Attribution 3.0 Unported License. The latest version of this and other scripts by the same author can be found at http://www.woollymittens.nl/
