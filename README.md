# | attach |

| attach | is a contact sharing website that anyone can fork and customize for their own. Fork this project and set up your own! Here is my personal [demo](https://attach.fly.dev)

-   [Installation](#installation)
-   [Development](#development)
-   [Deployment](#deployment)
    -   [Fly](#fly)
    -   [Locally](#locally)
-   [Runtime and Tools](#runtime-and-tools)
-   [Technologies](#technologies)
    -   [Frontend](#frontend)
    -   [Backend](#backend)

## Installation

Install [pre-reqs](#runtime-and-tools)

Then:

Run

```
git clone https://github.com/ZackarySantana/Attach.git attach
```

If it doesn't work, run

```
git clone git@github.com:ZackarySantana/Attach.git attach
```

Then make sure to cd (change directory) in to the attach folder

```
cd attach
```

Install the [technologies](#technologies) by running

```
npm install
```

<i>Make sure you have followed [installing and setting up fly](#fly)</i>

Setup your volume (this is so your stats can be persistent!)

```
fly volumes create stats_data -s 1
```

The "-s 1" stands for 1gb, the free version of fly only allows for 1g space but that's more than enough.

And deploy to the web with

```
fly launch
```

If you have already deployed it once, run

```
fly deploy
```

If either command fails, just run it again or message me for help!

For more info on deploying, head to [deploy with fly](#fly)

## Development

### Customization

Most of the customization will happen in [config.ts](./src/config.ts). This has the list of easily customizable things (all colors and gradients). I've made some themes at [color_themes.ts](./src/color_themes.ts). By default, the theme is randomly chosen each time the user accesses the website. You can change this functionality in the config!

If you would like to not randomize color themes, edit the config.ts to directly export the theme you want (copy and paste from the color_themes.ts or create your own in config.ts). As well, change [tailwind.config.js](./tailwind.config.js) to <i>not</i> include the line with `"./src/color_themes.ts",` so tailwind doesn't compile useless themes

You can also force a theme (if using the random option) by adding a search parameter (e.g. [https://attach.fly.dev/?theme=dracula](https://attach.fly.dev/?theme=dracula))

There's an additional, funky option you can add for themes that don't _fit_ the status quote (e.g. [https://attach.fly.dev/?funky=true](https://attach.fly.dev/?funky=true))

### `npm dev` or `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>

## Deployment

### Fly

Make sure to install [Fly.io](https://fly.io) (You don't need Docker to deploy this project!). You'll need to setup Fly by following their [docs](https://fly.io/docs/speedrun/).

### Locally

#### `npm run build`

Builds the app for production to the `dist` folder.<br>
It correctly bundles Solid in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

#### `npm run deploy`

Runs the app generated in the `dist` folder. This script uses the [host.js](./host.js) file to host all static files in dist on port `4173`.

## Runtime and Tools:

To install:

-   [Git](https://git-scm.com/) (Installation)
-   [Visual Studio Code](https://code.visualstudio.com/) (Recommended code editor)
-   [Node](https://nodejs.org/en/) v18.4.0
-   NPM v8.12.1 (comes with Node!)
-   [Flyctl](https://fly.io/docs/speedrun/) (Deployment)

If you have a mac, I recommend you install [homebrew](https://brew.sh/) and then run the following to install everything:

```
brew install git visual-studio-code node flyctl
```

Don't have to install:

-   [Docker](https://www.docker.com/) (The project just uses this tool but you don't need it installed locally)

## Technologies:

No need to try installing these, these are installed automatically when running `npm install`

### Frontend:

-   [Solid.js](https://solidjs.com) - Main Framework
-   [TypeScript](https://www.typescriptlang.org/docs/) - Main language
-   [Tailwind](https://tailwindcss.com/) - Used in all components

### Backend:

-   [Express](https://expressjs.com/) - Main server that handles all requests to the website
