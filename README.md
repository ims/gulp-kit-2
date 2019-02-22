# gulp-kit

Integrates [`node-kit`](https://github.com/jeremyworboys/node-kit)
with [`gulp 4`](http://gulpjs.com/) to compile
[`.kit`](http://incident57.com/codekit/help.html#kit) templates
with your own build system.

## Usage

    var kit = require('gulp-kit');
    const html = done => {
        src('src/kit/index.kit')
        .pipe(kit())
        .pipe(dest('dist/'));
        done();
    };
    exports.html = html;

## Options

You can turn off the default behaviour of
ignoring attempts to compile partials by
passing `{compilePartials : true}` to the
plugin.

      // ... as above
      .pipe( kit({compilePartials : true}) )
      // ... further pipes, as above

You can also pass through any user-defined CodeKit variables by passing
`{ variables: { key: value, key: value, etc. }}` to the plugin.

      // ... as above
      .pipe( kit({
          variables: {
    			"$uiVer": pkg.version,
    			"$bsVer": "3.1"
    	}}) )
      // ... further pipes, as above
