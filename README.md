# Build Commands

## **Main**

### **`gulp` or `gulp build` or `gulp build:assets`**

Build a assets directory.

**Sequenced Run Commands:**

    1. clean:assets
    2. build:images
    3. build:fonts
    4. build:scripts
    5. build:styles

*Note:* By default, the command `gulp build` alone runs as in Production mode. If you'd like to build files in Development mode, add flag `--dev` to command.

### **`gulp serve`**

Static server plus watch files.

**Sequenced Run Commands:**

    1. clean:jekyll
    1. build:assets
    1. build:jekyll
    2. watch

*Note:* By default, `gulp serve` runs as a Development(--dev) mode because its intended to run locally only. If you'd like to see what Production Build on `gulp serve` would look like, run with the `--test` flag.

### **`gulp watch`**

Watches for site changes to stream or rebuild static build. Uses **BrowserSync** to server static build, middleware for 404 errors and pretty/vanity urls, Self Signed Certificate for https. *Note:* By default, `gulp serve` runs as a Development Build because its intended to run locally only. If you'd like to see what Production Build on `gulp serve` would look like, run with the `--test` flag.

### **`gulp reload`**

Reloading via BrowserSync

### **`gulp clean`**

Deletes jekyll build `_site` and assets `assets` directories.

### **`gulp clean:assets`**

Deletes `assets` directories.

## **Jekyll**

### **`gulp build:jekyll`**

Runs the Jekyll build command.

### **`gulp clean:jekyll`**

Deletes Jekyll build `_site` directory.

## **Styles**

### **`gulp build:styles`**

Builds all site styles.

**Sequenced Run Commands:**

    1. build:styles:embed
    2. build:styles:main
    3. build:styles:css

### **`gulp build:styles:main`**

Main site SCSS stylesheets, the target import stylesheet is `_assets/styles/styles.scss`. Uses Sass compiler to process styles, adds vendor prefixes, minifies, then outputs file to the appropriate location for appropriate environments.

### **`gulp build:styles:embed`**

SCSS stylesheets for embedding styles throughout the theme. Any SCSS stylesheet that is prefixed with `embed-` will be processed then added to the `/assets/css` for usage. Use Jekyll Tag `{% embed_css src:'PATH' %}` to embed styles into markup.

### **`gulp build:styles:standalone`**

For vendor or plain css, add to the `_assets/styles/standalone` directory. This copies stylesheets to the build directory for usage.

### **`gulp clean:styles`**

Deletes all processed site styles.

## **Scripts**

### **`gulp build:scripts`**

Concatenates and uglifies global JS files and outputs result to the appropriate location for appropriate environments.

**Sequenced Run Commands:**

    1. lint:scripts
    2. build:scripts:main & build:scripts:standalone

### **`gulp build:scripts:main`**

Main site scripts; concatenates and uglifies global JS files and outputs result to the appropriate location for appropriate environments.

### **`gulp build:scripts:standalone`**

For vendor or plain scripts, add to the `_assets/js/standalone` directory. This copies scripts to the build directory for usage.

### **`gulp lint:scripts`**

Shows JS Lint warnings and errors based on the eslint `Prettier` plugin rules, see `.eslintrc`.

### **`gulp lint:scripts:fix`**

Fixes JS Lint warnings and errors based on the eslint `Prettier` plugin rules, see `.eslintrc`.

### **`gulp clean:scripts`**

Deletes all processed scripts.

## **Images**

### **`gulp build:images`**

Builds and optimizes all site images/files.

### **Sequenced Run Commands:**

    1. build:images:site
    2. build:images:media
    3. optimize:images

### **`gulp build:images:site`**

Copies theme specific images/files into image build directory. File types: `png, jpg, jpeg, gif, svg`

### **`gulp build:images:media`**

Copies uploaded media images/files into image build directory. File types: `png, jpg, jpeg, gif, svg, pdf, zip, eps`

### **`gulp optimize:images`**

Optimizes media and theme specific images/files.

### **`gulp clean:images`**

Deletes all processed images.

## **Fonts**

### **`gulp build:fonts`**

Copies fonts for `_assets/fonts` to font build directory.

### **`gulp clean:fonts`**

Deletes all processed fonts.
