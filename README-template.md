![npm](https://img.shields.io/npm/v/skelosaurus) ![npm bundle size (version)](https://img.shields.io/bundlephobia/min/skelosaurus/2.0.12) ![npm](https://img.shields.io/npm/dw/skelosaurus) ![GitHub last commit](https://img.shields.io/github/last-commit/ioncakephper/skelosaurus) ![GitHub](https://img.shields.io/github/license/ioncakephper/skelosaurus) ![Built with Docusaurus v2](https://img.shields.io/badge/Built%20with-Docusaurus%20v2-blueviolet)

![Outlined with Skelosaurus](https://img.shields.io/badge/Outlined%20with-Skelosaurus-red)


<!-- omit in toc -->
# skelosaurus
Skeleton documentation generator for Docusaurus v2 and v1

- [Installation](#installation)
- [Usage](#usage)
  - [`skelo -h`](#skelo--h)
  - [`skelo help build`](#skelo-help-build)
  - [`skelo help load`](#skelo-help-load)
  - [`skelo help save`](#skelo-help-save)
- [Quick example](#quick-example)
  - [Step 1: Create documentation project](#step-1-create-documentation-project)
  - [Step 2: Generate skeleton](#step-2-generate-skeleton)
  - [Step 3: Use skeleton documentation in Docusaurus](#step-3-use-skeleton-documentation-in-docusaurus)
- [Creating documentation folders](#creating-documentation-folders)
  - [Creating folders automatically](#creating-folders-automatically)
  - [Creating folders selectively](#creating-folders-selectively)
- [Creating `Overview` pages automatically](#creating-overview-pages-automatically)
- [Documentation](#documentation)
- [API](#api)
- [License](#license)

## Installation

Install the package globally:

```bash
npm i skelosaurus -g
```

The `skelo` command now available at the command prompt.

## Usage

### `skelo -h`

See commands and general options.

```txt
!import[/index-js-help.txt]
```

> **`build`** is the default command, so you can provide its  arguments and options without including the `build` command.


### `skelo help build`

See arguments and options for `build` command.

```txt
!import[/index-js-help-build.txt]
```

### `skelo help load`

See arguments and options for `load` command.

```txt
!import[/index-js-help-load.txt]
```

### `skelo help save`

See arguments and options for `save` command.

```txt
!import[/index-js-help-save.txt]
```

## Quick example

### Step 1: Create documentation project

Create a working folder `sample` and a documentation outline file `sample.md` which contains documention outline as Markdown.

```bash
mkdir sample
cd sample
echo Documentation outline for Docusaurus > sample.md
```

In `sample.md` copy the following:

```markdown
!import[/sample/sample.md]
```

Install Docusaurus in your working folder.

```bash
npx @docusaurus/init@next init sample-doc classic
```

This will create the `sample-doc` documentation project as inside your working folder.

### Step 2: Generate skeleton

Generate skeleton documentation with `skelo`:

```bash
skelo build sample -w ./sample-doc -d ./sample-doc/docs
```

The `sample\sample-doc\docs` folder contains `.md` topic source files for your documentation. The `sample\sample-doc\sidebars.js` contains the navigation description.

```txt
!import[/sample/tree.txt]
```

The `sample\sample-doc\sidebars.js` exports the sidebar navigation design.

```javascript
!import[/sample/sample-doc/sidebars.js]
```

The `sample\sample-doc\docs\introduction.md` has the front-matter Docusaurus expects, and is already filled with a lorem ipsum text.

```markdown
!import[/sample/sample-doc/docs/introduction.md]
```

### Step 3: Use skeleton documentation in Docusaurus

Open the `sample\sample-doc\docusaurus.config.js`, and edit the `themeConfig`:

```javascript
  themeConfig: {
    navbar: {
      title: 'My Site',
      logo: {
        alt: 'My Site Logo',
        src: 'img/logo.svg',
      },
      items: [
        {
          // to: 'docs/',
          to: 'docs/introduction',
          activeBasePath: 'docs',
          label: 'Docs',
          position: 'left',
        },
        ...
```

Now, start Docusaurus local server.

```bash
cd sample-doc
npm run start
```

Docusaurus does its magic and finally opens up the local documentation site it created. Click `Docs` item in the top navigation menu to see the navigation bar and basic content for each topic.

![Screenshot](./images/Screenshot%202020-10-24%20235147.png)

## Creating documentation folders

### Creating folders automatically

To create folders automatically, use the `-f` or `--autofolders` switch.

```bash
skelo sample -f -w ./sample-folders-doc -d ./sample-folders-doc/docs
```

> Because **`build`** is the default command, you can skip providing the command name explicityly, like in the example above. In the example above, `sample` is the outline filename. If the extension of the outline file is `.md`, you can skip writing it.

This will generate the documentation `.md` files and `sidebars.js` file as before, but it also creates a subfolder for each topic with items. Here is the folder structure in `sample/sample-folders-doc`:

```txt
!import[/sample/sample-folders-doc/tree.txt]
```

The `sample\sample-folders-doc\sidebars.js` is also changed to include the file paths.

```javascript
!import[/sample/sample-folders-doc/sidebars.js]
```

### Creating folders selectively

When you want to indicate a topic as a folder in which subtopics will go:

1. use the `@f` marker in your outline file
2. do NOT include the `-f` (`--autofolders`) switch in command line.

## Creating `Overview` pages automatically

Automatically insert an `Overview` documentation page as the first item in a navigation section or list of subtopics. This will save you time and make your documentation have a consistent look.

To create the `Overview` pages automatically, use the `-i` or `--intro` switch. By default, the title of the overview pages is set to `Overview`. You can specify a different title for the overview page with the `--introTitle` option.

```bash
skelo sample -i -f sample -w ./sample-folders-doc -d ./sample-folders-doc
```

## Documentation

See the official documentation at [https://skelosaurus.com](https://skelosaurus.com)

## API

!import[/index-js-jsdoc.md]

## License

!import[/LICENSE]


!export[/README.md]
