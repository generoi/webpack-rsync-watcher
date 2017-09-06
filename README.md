# webpack-rsync-watcher

Utility plugin for [`generoi/sage`](https://github.com/generoi/sage/) to rsync files when changed during the webpack watch task.

## Installation

Import the package in `resources/assets/build/webpack.config.watch.js`.

```js
const RsyncWatcher = require('webpack-rsync-watcher');
```

Add a setup event which initializes the watcher.

```js
new BrowserSyncPlugin({
  target,
  open: config.open,
  proxyUrl: config.proxyUrl,
  watch: config.watch,
  delay: 50,
  debouce: 800,
  events: {
    setup: (plugin) => (new RsyncWatcher(plugin.watcher, config.rsync)).watch(),
  },
}),
```
