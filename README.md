# Asynchronous-JavaScript
 
## Promise

### Promise is really async
```javascript
function doAsyncTask() {
  return Promise.resolve();
}

doAsyncTask().then(_ => console.log(message)); // <-- Unlike callbacks, promises are always async, result will be "Promise Resolved"
let message = "Promise Resolved";
```