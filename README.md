envify-test
===========

Test to show that `envify` prefers environment variable specified in the
`browserify.transform` field in `package.json` over something specified on the
command line.

    % npm install
    % npm run build


`package.json`:

    {
      "name": "envify-test",
      "version": "0.0.1",
      "description": "Testing envify inside of a package.json transform field",
      "author": "Chris Rawnsley",
      "license": "CC0-1.0",
      "repository": "https://github.com/casr/envify-test",
      "scripts": {
        "postinstall": "NODE_ENV='from env' browserify ."
      },
      "devDependencies": {
        "browserify": "13",
        "envify": "3"
      },
      "browser": "./browser.js",
      "browserify": {
        "transform": [
          ["envify", {"_": "purge", "NODE_ENV": "from transform"}]
        ]
      }
    }
