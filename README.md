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
### Chaining
```javascript
const promise = Promise.resolve("done")
promise
    .then(val=>{
    console.log(val)
    return "done2"
})
    .then(val=>console.log(val))
// 'done'
// 'done2'

```
Всё это работает, потому что вызов ```promise.then``` тоже возвращает промис, так что мы можем вызвать на нём следующий ```.then```.