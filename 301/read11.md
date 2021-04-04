# EJS
### Embedded JavaScript templating.

EJS is a simple templating language that lets you generate HTML markup with plain JavaScript. 

### Features
1. Fast compilation and rendering
2. Simple template tags: <% %>
3. Custom delimiters (e.g., use [? ?] instead of <% %>)
4. Sub-template includes
5. Ships with CLI
6. Both server JS and browser support
7. Static caching of intermediate JavaScript
8. Static caching of templates
9. Complies with the Express view system


### Get Started
##### Install

        $ npm install ejs

##### Use
Pass EJS a template string and some data. BOOM, you've got some HTML.

 
        let ejs = require('ejs');
        let people = ['geddy', 'neil', 'alex'];
        let html = ejs.render('<%= people.join(", "); %>', {people: people});

##### CLI
Feed it a template file and a data file, and specify an output file.

##### Reference 
* [EJS Tutorial](https://ejs.co/)
* [Watch EJS tutorial from WalkThroughCode on YouTube, Videos 1-5](https://www.youtube.com/playlist?list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)
* [Source Code for the EJS Tutorial](https://github.com/scotch-io/node-ejs)
* [Google Books API Docs]([ejs](https://developers.google.com/books/docs/v1/using#WorkingVolumes))

