# Travis CI with Angular Project

### 1.  First, install angular cli and create angular project with angular cli.

  [Angular CLI](https://cli.angular.io/)
  ```shell
  npm install -g @angular/cli
  ng new my-dream-app
  ```

### 2.  Create `.travis.yml` in the root

  <img src="https://github.com/zscfde/angular-with-travis/blob/master/README/travis.yml.png" width="400">

### 3.  Set the `.travis.yml`

  ```yml
  language: node_js

  node_js:
    - '12'

  script:
    - npm run test -- --watch=false --browsers=ChromeHeadlessNoSandbox
  ```

### 4.  Set `karma.conf.js` for ChromeHeadlessNoSandbox

  ```js
  module.exports = function(config) {
    config.set({
      browsers: ['Chrome', 'ChromeHeadless', 'ChromeHeadlessNoSandbox'],

      // you can define custom flags
      customLaunchers: {
        ChromeHeadlessNoSandbox: {
          base: 'ChromeHeadless',
          flags: ['--no-sandbox']
        }
      }
    });
  };
  ```

#### reference:

- [https://docs.travis-ci.com/user/tutorial/](https://docs.travis-ci.com/user/tutorial/)
- [https://docs.travis-ci.com/user/languages/javascript-with-nodejs/](https://docs.travis-ci.com/user/languages/javascript-with-nodejs/)
- [https://docs.travis-ci.com/user/chrome](https://docs.travis-ci.com/user/chrome)
- [https://medium.com/faun/configuring-travis-ci-for-angular-application-34afee1715f](https://medium.com/faun/configuring-travis-ci-for-angular-application-34afee1715f)
