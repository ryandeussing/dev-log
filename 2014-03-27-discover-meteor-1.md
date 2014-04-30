## Getting Started

In Ruby terms, Meteorite is like `rubygems`, Atmoshphere is like `rubygems.org`

Meteorite gives you the `mrt` executable, for installing packages and creating apps that use Meteorite.

`mrt create microscope`

`cd microscope`

`meteor` to run the app

`mrt add bootstrap` to add smart package

### Packages
- core packages (guts)
- smart packages (included with meteor - `meteor list` to list)
- local packages (roll your own, put them in `/packages`)
- atmosphere smart packages (third party, you need meterite to install them)
- NPM packages (node.js packages that might work with the above packages)

### File structure (suggested)

```
/app
  - /client
    - main.html
    - main.js
  - /server
  - /public
```

Code in the `/server` directory only runs on the server.

Code in the `/client` directory only runs on the client (css lives here)

Everything else runs on both the client and server.

Files in `/lib` are loaded _before_ anything else.

Any `main.*` file is loaded _after_ everything else.

Your static assets (fonts, images, etc.) go in the `/public` directory.

### Templates

This is what including a template looks like:

    <div id="main" class="row-fluid">
      {{> postsList}}
    </div>

