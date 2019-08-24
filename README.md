# ng-at-internet-ui-router-plugin

> Plugin for ATInternet when using ui-router.

[![Downloads](https://badgen.net/npm/dt/@ovh-ux/ng-at-internet-ui-router-plugin)](https://npmjs.com/package/@ovh-ux/ng-at-internet-ui-router-plugin) [![Dependencies](https://badgen.net/david/dep/ovh-ux/ng-at-internet-ui-router-plugin)](https://npmjs.com/package/@ovh-ux/ng-at-internet-ui-router-plugin?activeTab=dependencies) [![Dev Dependencies](https://badgen.net/david/dev/ovh-ux/ng-at-internet-ui-router-plugin)](https://npmjs.com/package/@ovh-ux/ng-at-internet-ui-router-plugin?activeTab=dependencies) [![Gitter](https://badgen.net/badge/gitter/ovh-ux/blue?icon=gitter)](https://gitter.im/ovh/ux)

## Install

```sh
yarn add @ovh-ux/ng-at-internet-ui-router-plugin
```

## Usage

```js
import angular from 'angular';
import ngAtInternetUiRouterPlugin from '@ovh-ux/ng-at-internet-ui-router-plugin';

angular
  .module('myApp', [
    ngAtInternetUiRouterPlugin,
  ]);
```

Follow [at-internet installation](https://github.com/ovh-ux/ng-at-internet/blob/master/README.md)
In your web page:

```html
<script src="angular.js"></script>
<script src="smarttag-yourproject.js"></script>
<script src="dist/umd/ng-at-internet.js"></script>
<script src="dist/umd/ng-at-internet-ui-router-plugin.js"></script>
```

## Examples

Please see at-internet documentation:
[link](https://github.com/ovh-ux/ng-at-internet/blob/master/README.md)

Configuring the provider:

```js
app.config(['atInternetUiRouterPluginProvider', function (provider) {
  provider.setTrackStateChange(true);
}]);
```

That's it, now every state change will send a page tracking data to ATInternet.
To disabled tracking on specific states, use the following syntax:

```js
$stateProvider.state('your-untracked-state', {
  url: '...',
  atInternet: {
    ignore: true, // this tell AtInternet to not track this state
  },
});
```

By default, the state name will be used for the page name to be sent. If you want to modify this behavior
for a given state, please use the following syntax :

```js
$stateProvider.state('your-state', {
  url: '...',
  atInternet: {
    rename: 'foobar', // use "foobar" as page name instead of "your-state"
  },
});
```

If you want, you can apply some filters on the states name, for example :

```js
app.config(/* @ngInject */ (atInternetUiRouterPluginProvider) => {
  // replace all occurrences of "foo" by "bar" in states name
  atInternetUiRouterPluginProvider
    .addStateNameFilter((stateName) => stateName.replace(/foo/g, 'bar'));
});
```

## Test

```sh
yarn test
```

## Contributing

Always feel free to help out! Whether it's [filing bugs and feature requests](https://github.com/ovh-ux/ng-at-internet-ui-router-plugin/issues/new) or working on some of the [open issues](https://github.com/ovh-ux/ng-at-internet-ui-router-plugin/issues), our [contributing guide](CONTRIBUTING.md) will help get you started.

## License

[BSD-3-Clause](LICENSE) © OVH SAS
