# Create a Next.js App
To build a complete web application with React from scratch, there are many important details you need to consider:

Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel. You need to do production optimizations such as code splitting. You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering. You might have to write some server-side code to connect your React app to your data store.

A framework can solve these problems. But such a framework must have the right level of abstraction — otherwise it won’t be very useful. It also needs to have great "Developer Experience", ensuring you and your team have an amazing experience while writing code

Setup First, let’s make sure that your development environment is ready.

If you don’t have Node.js installed, install it from here. You’ll need Node.js version 10.13 or later. You’ll be using your own text editor and terminal app for this tutorial. If you are on Windows, we recommend downloading Git for Windows and use Git Bash that comes with it, which supports the UNIX-specific commands in this tutorial. Windows Subsystem for Linux (WSL) is another option.

Create a Next.js app To create a Next.js app, open your terminal, cd into the directory you’d like to create the app in, and run the following command:
`npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn-starter/tree/master/learn-starter"`

Create a Next.js App Setup First, let’s make sure that your development environment is ready.

If you don’t have Node.js installed, install it from here. You’ll need Node.js version 10.13 or later. You’ll be using your own text editor and terminal app for this tutorial. If you are on Windows, we recommend downloading Git for Windows and use Git Bash that comes with it, which supports the UNIX-specific commands in this tutorial. Windows Subsystem for Linux (WSL) is another option.


Create a Next.js app To create a Next.js app, open your terminal, cd into the directory you’d like to create the app in, and run the following command:

npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn-starter/tree/master/learn-starter"

Under the hood, this uses the tool called create-next-app, which bootstraps a Next.js app for you. It uses this template through the --example flag.

If it doesn’t work, please take a look at this page.

Run the development server You now have a new directory called nextjs-blog. Let’s cd into it:

`cd nextjs-blog`
Then, run the following command:

`Then, run the following command:`
Then, run the following command: