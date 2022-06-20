### What is Promise? 

You can find different tricky tasks for determining execution order in the code below. 


#### Task 1. Level: Medium

```javascript
Promise.resolve(10)
  .then(e => console.log(e)) // ??
  .then(e => Promise.resolve(e))
  .then(console.log) // ??
  .then(e => {
    if (!e) {
      throw 'Error caught';
    }
  })
  .catch(e => {
    console.log(e); // ??
    return new Error('New error');
  })
  .then(e => {
    console.log(e.message); // ??
  })
  .catch(e => {
    console.log(e.message); // ??
  });
```

Answer: 10, undefined, 'Error caught', 'New error'


#### Task 2. Level: Easy

```javascript
(function() {
    console.log(1); 
    setTimeout(function(){console.log(2)}, 1000); 
    setTimeout(function(){console.log(3)}, 0); 
    console.log(4);
})();
```

Answer: 1, 4, 3, 2

#### Task 3. Level: Medium

```javascript
const myPromise = (name) => Promise.resolve('I have resolved! ' + name)

function firstFunction() {
    myPromise("firstFunction").then(res => console.log(res));
    console.log('first');
}

async function secondFunction() {
    console.log(await myPromise("secondFunction"));
    console.log('second');
}

firstFunction()
secondFunction()
```

Answer: `first`, `I have resolved! firstFunction`, `I have resolved! secondFunction`, `second`

#### Task 4. Hard

```javascript
const intervalId = setInterval(() => {
  console.log('James');
}, 10);

setTimeout(() => {
  const promise = new Promise((resolve) => {
    console.log('Richard');
    resolve('Robert');
  });

  promise
    .then((value) => {
      console.log(value);

      setTimeout(() => {
        console.log('Michael');

        clearInterval(intervalId);
      }, 10);
    });

  console.log('John');
}, 10);
```

Answer: `James`, `Richard`, `John`, `Robert`, `James`, `Michael` 
