[Website of Electron][Electron's site]
[Download the PDF version of this ReadMe file](newElectronProject.pdf)

# **Electron**: Creating a new project

<br>

> [!NOTE]
> Before the fun, **create** a GitHub **repository** if you want to

<br>

## And the party begin 🚀

> Let's **initialize** the **project**

```sh
npm init -y
```

> Now, **install** the **dependencies**

```sh
npm install --save-dev electron
npm install --save-dev @electron-forge/cli
```

> [!CAUTION]
> **Create** a **.gitignore** with **Node.js**, append with **VSCode**, then **type**:

```sh
echo >> .gitignore
echo '# CUSTOMS' >> .gitignore
echo '.DS_Store' >> .gitignore
echo 'Thumbs.db' >> .gitignore
```

> [!WARNING]
> Go on, **edit** `package.json`: add `main` **&** `dev` lines:

```js
  "license": "ISC",
  "author": "jerem.re",
  "type": "commonjs",
  "main": "main.js",
  "scripts": {
    "dev": "electron ."
  },
```

<br>

## Add your touch, your breath, your logo 🤩

> **Place** your **icon** in a folder (`./assets/img/` *recommended*)

> [!IMPORTANT]
> The app icon must be at least 1024x1024 for better results

> Let's install an icon generator

```sh
npm install --save-dev electron-icon-builder
```

> By the way, generate the icons
```sh
./node_modules/.bin/electron-icon-builder
--input=/path/to/icon.png --output=res
```

<br>

## Get things ready before distributing 🤑

> **Initialize** the **packaging tool**

```sh
npx electron-forge import
```

> In `forge.config.js`, let's add:

```js
  packagerConfig: {
    // The app icon.s must be placed in the following folers or wherever:
    icon: 'path/to/the/mac/icon'
    icon: 'path/to/the/windows/icon'
    icon: '...'
    // The icon.s must be in the same folder that the one above
    // AND.. the extension is not required here, voilààà
  },
```

<br>

## Supercharge with frameworks or tools 🥳

> **Bootstrap** & **Bootswatch** integrations

**Untouched** version of **BootStrap** [CSS](css/bootstrap.css) & [JS](js/bootstrap.js) (5.3.3)

Version of the **Bootswatch Sketchy** theme [here](css/bootswatch.css)
(slightly touched cause the **fonts refused to work**)

Speaking of which, there are the choosen ones:

[Cabin Sketch Regular](fonts/CabinSketchRegular.woff2)

[Cabin Sketch Bold](fonts/CabinSketchBold.woff2)

& [Neucha Regular](fonts/NeuchaRegular.woff2)

Also avialable [here][Google Fonts' site] as they are Google Fonts

<br>

## Without main, no Electron app, no app: no app 😣

> The `main.js` file to **run** the **application** looks like this:

```js
// Initialize & declare the prerequisites
const { app, BrowserWindow } = require('electron/main')

// Create a new window
const createWindow = () => {
    const win = new BrowserWindow({
        // Show the icons to close or minimize the window when hovering the top corner
        titleBarStyle: 'customButtonsOnHover',
        // Move a little bit these icons to work with the design
        trafficLightPosition: { x: 8, y: 8 },
        // Set big dimensions to make the window as big as the device's screen
        width: 99999,
        height: 99999
    })

    // Loading the created window with this HTML
    win.loadFile('index.html')
}

// Launch the window when the app is ready
app.whenReady().then(() => {
    createWindow()

    // Mac part: ensure the default closing behaviour is respected
    app.on('activate', () => {
        if (BrowserWindow.getAllWindows().length === 0) {
            createWindow()
        }
    })
})

// Windows & Linux part: ensure the app quits when the close button is fired
app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit()
    }
})
```

<br>

## Just a little start point 😎

> The `head` tag of `index.html` looks like:

```html
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="assets/css/bootstrap.css">
    <link rel="stylesheet" type="text/css" href="assets/css/bootswatch.css">
    <link rel="stylesheet" type="text/css" href="assets/css/style.css">
    <link rel="shortcut icon" href="assets/img/fav.png" type="image/x-icon">
</head>
```

> And the part before the closing `body` tag

```html
    <script src="assets/js/app.js"></script>
    <script src="assets/js/bootstrap.js"></script>
```

<br>

### [/jerem.re][My website] 🥰

&copy; MMXXV

<br>

Let's cooooooode !!!!!!! 🧑‍💻
---

[Electron's site]: https://www.electronjs.org/
[Google Fonts' site]: https://fonts.google.com/share?selection.family=Cabin+Sketch:wght@400;700%7CNeucha
[My website]: https://www.jerem.re/
