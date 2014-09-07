Shopify makes designing/developing themes harder than it has to be:

• you can't design locally, you have to push changes to their server and view yoru work there (you know, like it's 1996)
• they built a tool called Timber to give developers a ready-to-go environment, but instead of using tools people actually use (like Bootstrap or Foundation), they chose an obscure css grid system that exaclty nobody uses, and which laves out things you probably want (i.e. carousel js, etc.)

So, here's the way to get Bootstrap working while designing a Shopify store:

1. use this: https://github.com/Shopify/shopify-css-import - which basically copies css/scss files from one folder to another, where they get uploaded. It's not supposed to upload files that start with an underscore, but it does.

2. dump Bootstrap's scss files into your project, but without any directories, and then fix all the `import url()` paths so they work. I also removed a file called `_theme.scss` which I think has to do with creatig custom versions of Bootstrap and was causign an issue.

3. you still have to wait for yoru .scss files to upload to Shopify and view your shit online

Don't forget:
 - override Bootstrap's defaults with your own styles as needed
 - maybe borrow minification/uglification from yeoman's gulpfile so your deployed code is tight