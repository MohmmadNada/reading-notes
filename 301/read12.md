# EJS Partials
reuse the same HTML across multiple views. as footer and header , nav bar ,the same for all pages . 
we put it in ejs file as templates

>Note: The <%- %> tags allow us to output the unescaped content onto the page (notice the -). This is important >when using the include() statement since you don’t want EJS to escape your HTML characters like ‘<’, ‘>’, etc…

        <!-- views/post.ejs -->
           <!DOCTYPE html>
           <html>
           <head>
              <meta charset="utf-8">
                <title>POST_TITLE | Node.js Blog</title>
             <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
             <style>
                    body {
                        padding-top: 20px;
                     padding-bottom: 20px;
                 }
             </style>
         </head>
          <body>
             <div class="container">
                    <%- include('partials/navbar') %>
                    <div>
                        <h2>POST_TITLE</h2>
                        <p>by <a href="#">POST_AUTHOR</a></p>
                        <p>POST_CONTENT</p>
                        <hr>
                   </div>
            <%- include('partials/footer') %>
                   </div>
          </body>
          </html>


 I’ve intentionally left in some placeholders such as LIST_OF_POSTS, POST_TITLE, POST_AUTHOR, and POST_CONTENT so that we can take a look at how we can pass data from our Node + Express application to our views in the next section.