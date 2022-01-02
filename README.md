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
Всё это работает, потому что вызов ```promise.then``` тоже возвращает промис, так что мы можем вызвать на нём следующий ```.then```. Без строки ``` return "done2" ``` вернуло бы не ``` "done2" ``` а ``` 'undefined' ```

* Don't chaining
```javascript
const promise = Promise.resolve("done")
promise.then(val=>{
    console.log(val)
    return "done2"
})
promise.then(val=>console.log(val))
// 'done'
// 'done'

```
Все обработчики ```.then``` на одном и том же промисе получают одно и то же значение – результат выполнения того же самого промиса. 

### TASKS

```javascript
async function getPosts(){
    let response = await fetch('https://jsonplaceholder.typicode.com/users')
    return await response.json()
}
async function getUsers(){
    let response = await fetch('https://jsonplaceholder.typicode.com/users')
    return await response.json()
}

Promise.all([getPosts(), getUsers()]).then(console.log)
// [Array(10), Array(10)] 
// array of arrays

Promise.allSettled([getPosts(), getUsers()]).then(console.log)
// 0: {status: 'fulfilled', value: Array(10)}
// 1: {status: 'fulfilled', value: Array(10)}
// array of objects
```