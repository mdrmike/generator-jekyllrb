# Generator-jekyll-github

**FORKED FROM:**   [Jekyllrb](https://github.com/robwierzbowski/generator-jekyllrb)—Differences include updates to focus on Jekyll 3 and [Github Pages](https://jekyllrb.com/docs/github-pages/).


**Supercharge Jekyll 3 & native Github-pages development with Yeoman. Yo, Jekyll-github!**

Generator-jekyll-github wraps the [Jekyll](http://jekyllrb.com/) static site generator in a [Yeoman](http://yeoman.io/) development workflow. Scaffold your site with Yo, manage front end packages with [Bower](http://bower.io/), and automate development and build tasks with [Grunt](http://gruntjs.com/).

Generator-jekyll-github is ideal for developing high performance static sites and prototyping dynamic sites and apps (especially if the final version uses Yeoman too). It's also a great introduction to Yeoman if you're not familiar with JavaScript MV* frameworks.

## FAQ

Common problems? Common questions? Check out the [FAQ.md](FAQ.md)

## Features

**During setup you can choose:**

- [Compass](http://compass-style.org/), [Sass](http://sass-lang.com/), or vanilla CSS
- [CoffeeScript](http://coffeescript.org/) or vanilla JavaScript
- Automatic CSS vendor prefixing with [Autoprefixer](https://github.com/ai/autoprefixer)
- Default Jekyll or [HTML5 Boilerplate](http://html5boilerplate.com/) templates
- Common Jekyll configuration options

**Generator-jekyllrb always includes:**

- Built in preview server with [BrowserSync](http://www.browsersync.io/)
- Automatic Jekyll and preprocessor compiling
- Code quality checks with [Jshint](http://www.jshint.com/) and/or [CoffeeLint](http://www.coffeelint.org/), [CssLint](http://csslint.net/), and `jekyll doctor`
- An automatic build process that includes concatenation, image optimization, CSS and HTML minification, JS uglification, and asset revving to bust those caches

## Getting Started

- generator-jekyllrb requires [Node.js](http://nodejs.org/) `>= 0.10`, [Ruby](http://www.ruby-lang.org/) `>= 1.9`
- Install the generator: `npm install -g generator-jekyllrb`
- Run: `yo jekyllrb`

## Grunt Workflow

#### grunt serve

Compiles all files and opens the site in your default browser. A watch task watches for changes to files, recompiles if necessary, and injects the changes into the browser with LiveReload.

#### grunt check

Checks code quality with Jshint and CSS Lint, and Jekyll health with `jekyll doctor`.

#### grunt build

Builds an optimized site to the dist directory. [Usemin blocks](https://github.com/yeoman/grunt-usemin#the-useminprepare-task) are concatenated, [CSS](https://github.com/gruntjs/grunt-contrib-cssmin), [images](https://github.com/gruntjs/grunt-contrib-imagemin), and [HTML](https://github.com/gruntjs/grunt-contrib-htmlmin) are minified, [JavaScript is uglified](https://github.com/gruntjs/grunt-contrib-uglify), and assets are [revved](https://github.com/yeoman/grunt-filerev) for cache busting.

`grunt serve:dist` will run `grunt build` and open the result in your default browser

#### grunt deploy

During scaffolding the generator gives you the option to configure [grunt-build-control](https://github.com/robwierzbowski/grunt-build-control) to version and deploy your built code to a remote repository. If you configure build-control, `grunt deploy` will run `grunt check`, `grunt test`, `grunt build`, and then commit and deploy your built code to the specified remote repository.

#### grunt (default)

`grunt` on its own is a special task that runs `grunt check`, any tests you've added, and `grunt build`.

#### Individual tasks and :targets

Every task and target in the Gruntfile can be run individually (e.g., `grunt jshint:all` or `grunt compass:server`). Edit the tasks and [add new ones to fit your needs](http://gruntjs.com/configuring-tasks).

## Bower, components, and Usemin

[Bower](http://bower.io/) is a package manager for front-end components. Use it to download and manage CSS, JavaScript, and [preprocessor tools](https://github.com/Team-Sass) for your site. Everything in the _bower_components directory is available while running `grunt serve`.

To include components in the build, place them inside of a Usemin block or add them to the `copy:dist` task. This workflow will be streamlined with the release of Usemin 2.0.

## More on Yeoman and Grunt

[Getting started with Yeoman](http://yeoman.io/learning/index.html)  
[Getting started with Grunt](http://gruntjs.com/getting-started)

## Migrating an existing site

Wrapping an existing site in Yeoman isn't hard, but it takes a little manual editing.

1. Generate a new Yeoman/Jekyll app with the same tools and directory structure as your own. Ignore the templating options.
1. Transfer any custom configuration from your _config.yml to the newly generated _config.yml.
1. If you're using Compass, transfer custom configuration from your config.rb to the `compass` task in the Gruntfile.
1. Delete everything inside the Yeoman app directory.
1. Delete your site's original _config.yml, config.rb, and any files generated by Jekyll, CSS preprocessors, or CoffeeScript. Copy the remaining site into the app directory.
1. Wrap any asset references in your copied layout files with [usemin blocks](https://github.com/yeoman/grunt-usemin#blocks). The asset target paths you enter in `usemin` blocks should match the paths you entered during setup, as these are now expected by `usemin`, `autoprefixer` and other task configurations in your Gruntfile.
1. Test that everything is working correctly by running `grunt serve`, `grunt dist`, and `grunt serve:dist`. Check that the files you expect are being transferred to the dist directory.
1. If you were versioning the _site directory, move its .git folder to the dist directory.

## Notes

#### Nested asset directories and Jekyll

Jekyll [can't exclude nested directories](https://github.com/jekyll/jekyll/issues/906), so we must exclude all directories that match the innermost asset directory. For example, `assets/css` will exclude all directories named `css` from Jekyll compilation. This will cause issues if your site has a tag or category named `css`; if you're worried about accidental exclusions prefix all asset directories with an underscore (`assets/_css`).

#### Absolute path to assets in CSS

Since we revision assets such as images, make sure that your CSS calls them using their absolute path, so on ``grunt build`` those images will be replaced properly.

Incorrect:
```css
body {
  background: url('../images/foo.jpg');
}
```

Correct:
```css
body {
  background: url('/images/foo.jpg');
}
```

## Contribute

**[Please read the contributing guidelines before posting an issue.](https://github.com/robwierzbowski/generator-jekyllrb/blob/master/CONTRIBUTING.md)**

Post bugs and feature requests to the [Github issue tracker](https://github.com/robwierzbowski/generator-jekyllrb/issues). In lieu of a formal styleguide, take care to maintain the existing coding style. Lint and test your code using [Grunt](https://github.com/gruntjs/grunt).

## Release History

[Changelog](//github.com/robwierzbowski/generator-jekyllrb/blob/master/CHANGELOG)

## License
[BSD-new](http://en.wikipedia.org/wiki/BSD_License)


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/robwierzbowski/generator-jekyllrb/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
