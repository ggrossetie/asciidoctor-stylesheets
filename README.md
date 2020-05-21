# Asciidoctor stylesheets

[![Build](https://github.com/Mogztter/asciidoctor-stylesheets/workflows/Build/badge.svg)](https://github.com/Mogztter/asciidoctor-stylesheets/actions?query=workflow%3ABuild)


This project is a factory for stylesheets that can be used to style the HTML generated by an AsciiDoc processor (specifically the html5 backend).
In addition to being a general purpose AsciiDoc stylesheet generator, it is used to generate the default stylesheet that is bundled with Asciidoctor.

## Usage

    $ npm i asciidoctor-stylesheets

All the stylesheets will be available in the `node_modules/asciidoctor-stylesheets/css`.

**TIP:** If you are using Sass, you can import the Sass files from the `node_modules/asciidoctor-stylesheets/sass` directory.

## Setup and compilation

To setup the project, make sure you have Node.js and npm (or yarn) installed.
Next, run `npm` to install the required dependencies:

    $ npm i

Once you have the dependencies installed, you can build the stylesheets.

## Build the stylesheets

To build the stylesheets, run:

    $ npm run build

The stylesheets are compiled from the Sass source files in the `sass/` folder and written to the `css/` folder.
You can then reference the stylesheets in `css/` from your HTML file.

## Create sample documents

First, create a sample AsciiDoc file, such as:

```adoc
= Introduction to AsciiDoc
Doc Writer <doc@example.com>

A preface about http://asciidoc.org[AsciiDoc].

== First Section

* item 1
* item 2

[source,ruby]
puts "Hello, World!"
```

**TIP:** Alternatively, you can use this README as an example.

Then, use AsciiDoc or Asciidoctor to generate HTML that uses one of the stylesheets from the +css/+ directory:

    $ asciidoctor -a stylesheet=./css/asciidoctor.css sample.adoc

If you want to activate syntax highlighting in the code, add this argument:

    -a source-highlighter=highlightjs

Now just browse to +sample.html+ in your browser and checkout the result!

## External preview

You may want to preview sample HTML files on another computer or device.
To do that, you need to serve them through a web server.
You can quickly serve HTML files in the root directory of the project using the following command:

    python -m SimpleHTTPServer 4242

## Create a new theme

Themes go in the `sass/` folder.
To create a new theme (e.g., `hipster`), start by creating two new files:

`sass/hipster.scss`
 * Imports the theme settings, which includes default variables and resets
 * Imports the AsciiDoc components
 * Defines any explicit customizations

`sass/settings/_hipster.scss`
 * Sets variables that customize the AsciiDoc CSS components

Here's a minimal version of `sass/hipster.scss`:

```scss
@import "settings/hipster";
@import "components/asciidoc";
@import "components/awesome-icons";
```

**NOTE:** You don't have to include the underscore prefix when importing files.

You can add any explicit customizations below the import lines.

The variables you can set in `sass/settings/_hipster.scss` are defined in the [global settings and imports for the AsciiDoc components](https://github.com/mogztter/asciidoctor-stylesheets/blob/master/sass/settings/_defaults.scss).

Happy theming!
