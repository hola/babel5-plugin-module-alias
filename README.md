# Module alias plugin for Babel 5

A [babel](http://babeljs.io) plugin to easily map directories as different directories when your required a module.
Useful when you don't want to write relative path yourself.

This is a fork of
[babel-plugin-module-resolver](https://github.com/tleunen/babel-plugin-module-resolver)
before it was changed, with the extra functionality of `npm:` aliasing working.
It's a drop in replacement for `babel-plugin-module-alias` version 0.2.1.


## Usage

Instead of writing `var m = require('../../../../utils/myUtils')` or `import m from '../../../../myUtils'`. This plugin will allow you to set an alias to access your plugin.
```js
var myUtils = require('utils/myUtils');
// or
import myUtils from 'utils/myUtils';
```

To do so, first install babel and the plugin
```
$ npm install --save babel babel-plugin-module-alias
```

Then, the recommended way of using it is by using the file `.babelrc` to setup the configuration for Babel.
```json
{
  "plugins": [
    "babel-plugin-module-alias"
  ],
  "extra": {
    "module-alias": [
      { "src": "./src/utils", "expose": "utils" }
    ]
  }
}
```

Module aliasing also works for a single modules. Given this config in `.babelrc`:

```json
{
  "plugins": [
    "babel-plugin-module-alias"
  ],
  "extra": {
    "module-alias": [
      {
        "src": "../some-path/more-folders/my-awesome-lib",
        "expose": "my-awesome-lib"
      }
    ]
  }
}
```

In your code you can simply do:

```js
import MyAwesomeLib from 'my-awesome-lib'; 
```

_Note:_ the section `extra` is a custom section commonly used by plugins to take options. There's currently no better way in Babel to pass options to plugins.

## License

MIT, see [LICENSE.md](/LICENSE.md) for details.
