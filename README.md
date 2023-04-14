# Microbox Bootstrap Landing Page Generator

This project is used to generate static HTML pages and accompanying assets for Microbox quickstarts/bootstraps. It's built using [Middleman](https://middlemanapp.com/) and is designed to run using [Microbox](https://microbox.cloud). If you haven't already, [create a free Microbox account](https://dashboard.microbox.cloud/users/register) and [download and install Microbox](https://dashboard.microbox.cloud/download).

## Start the Project
From the root of the the project, run:

```bash
# add a convenient way to access the app in a browser
microbox dns add local bootstrap-landing.dev

# start Microbox and drop into a console
microbox run

# start the middleman server
middleman
```

## Generating the Static Files
To generate all the static files, from inside the Microbox console, run:

```bash
middlman build
```

All static files will be generated in the `build` directory. **When including them in the actual projects, be sure to update the stylesheet and favicon paths in the** `<head>`.

## Adding New Projects
Projects are organized by language. Each project needs the following files:

#### \_logo.erb
This is simply an `svg` file renamed with the `.erb` so Middleman can load it into the template as a partial.

#### favicon.png
Simply favicon using the project icon. It should be 32px × 32px.

#### index.html.haml
While this is used to generate the actual page, it only contains yaml front-matter and basically serves as a variable declaration file. Each `index.html.x` must include the following:

```yaml
---
project: Project Name
language: Runtime Language
more_info:
  links:
    - text: Link Text
      href: Link href
---
```

#### styles.scss
This to is used to generate the css for each landing page, but really only serves as a variable declaration file. It must contain the following:

```scss
@import "../../stylesheets/base";

// Colors
$bg-left: #333;     // Background Grandient Left
$bg-right: #000;    // Background Grandient Right
$burst: #fff;       // Burst Line Color
$shadow: #000;      // Icon Shadow Color
$heading: #fff;     // H2 $ H4 Color
$text: #999;        // Text Color
$link: #999;        // Link Color
$link-hover: #fff;  // Link Hover Color

@import "../../stylesheets/project-template"
```
