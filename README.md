# LocalMonitor
LocalMonitor is an error tracking and performance monitoring tools, suitable for localization and Private deployment project.

# General
``` jsx
import React from 'react'
import { createRoot } from 'react-dom/client';
import LocalMonitor from 'react-local-monitor';

// react <= 18
LocalMonitor.init({
    // Local storage type, localstorage sessionstorage indexdb， Default IndexDB, then downgrade compatibility
    storage: 'indexdb',
    // 阈值
    max: 2000,
    // 抽样
    sample: 1,
})

const container = document.getElementById('app');
const root = createRoot(container);
root.render(<App />);
```

``` jsx
// React 19
const container = document.getElementById('app');
const root = createRoot(container, {
    onUncaughtError: LocalMonitor.reactErrorHandler(),
    onCaughtError: LocalMonitor.reactErrorHandler(),
    onRecoverableError: LocalMonitor.reactErrorHandler(),
});
root.render(<App />);
```
