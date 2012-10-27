# Wallπ
![](https://dl.dropbox.com/u/4905073/web%20UI.png)

## About the Hack
Wallπ uses frequency analysis to draw a visual, circular representation of an album. The amount of activity within a frequency is reflected in the density of the color. The colour used to draw the circle is extracted from the cover art. The output file (at the moment) is 3508x4961px, high enough for print.

I'm _not_ using FFT data unfortunately: Some research and a lot of frustration at a previous hackday taught me that there are no good API's for Processing or Javascript which would allow me to get frequency data in a non-realtime fashion, so this time I decided to use The Echonest's segment pitch analysis.

**A hosted version might come soon**

## How to run
There is a server component which is used to proxy remote assets (to prevent cross-domain issues) and serve the html and assets. This component is written in Node. You can use `npm install` to install the neccesary dependencies. After all the dependencies are installed, type `bin/server` to run. It's then available at `localhost:9100`. Open index.html for instructions on how to load an album.

After the image has loading, your browser might crash a lot, the only way to export the image that I found to _not_ crash the browser is by copying the image and pasting it in Photoshop or a similar application.

## Configuration
There are a number of configuration options you might want to set to experiment with to get the desired result, here's a lazy copy/paste from `main.js`:

    // used to multiply/divide certain values:
    // - scaling the canvas down after rendering (for preview purposes)
    // - scaling up font and whitespace size as it appears in the preview
    scaleFactor       : 8,
    // Reduces the amount of data with this factor
    slimFactor        : 2,
    // Space in px between the edge of the canvas/paper & circle
    whitespace        : 30,
    // space in px on the inside, makes for interesting effects
    innerDiameter     : 0,
    // Minimum opacity of every line in the circle
    minimumOpacity    : 0.3,
    // Wether we should use a "light" or "dark" background.
    colorScheme        : 'light',
    // Distance of the text from the circle
    textDistance       : 30,
    // Speaks for itself, I'm using Neutra locally.
    font               : 'Helvetica Neue'

## Todos
-  Automatically fetch cover art & track titles for an album
-  Don't use opacity to show intensity, but mix it with white/black instead.
-  Prettier results with very light and very dark colours
-  Render stuff as vectors instead
-  Different layouts
