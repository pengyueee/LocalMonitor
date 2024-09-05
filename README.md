# LocalMonitor
LocalMonitor is an error tracking and performance monitoring tools, suitable for localization and Private deployment project.

# General

react <= 18
``` jsx
import React from 'react'
import { createRoot } from 'react-dom/client';
import LocalMonitor from 'react-local-monitor';

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

React 19
``` jsx
const container = document.getElementById('app');
const root = createRoot(container, {
    onUncaughtError: LocalMonitor.reactErrorHandler(),
    onCaughtError: LocalMonitor.reactErrorHandler(),
    onRecoverableError: LocalMonitor.reactErrorHandler(),
});
root.render(<App />);
```

class usage
``` jsx
class App extends React.Component {
    render() {
      return (
        <LocalMonitor.ErrorBoundary fallback={FallbackComponent}>
            <OtherComponents />
        </LocalMonitor.ErrorBoundary>
      );
    }
}
```
