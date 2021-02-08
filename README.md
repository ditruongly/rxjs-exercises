# Exercise 7

```javascript
function subscribe(subscriber) {
  const intervalId = setInterval(() => {
    subscriber.next("hi");
  }, 1000);

  return function unsubscribe() {
    clearInterval(intervalId);
  };
}

const unsubscribe = subscribe({ next: x => console.log(x) });

// Later:
unsubscribe(); // dispose the resources

```
Write the same behavior above, but with Observables
<details>
<summary>Solution</summary>

```javascript
import { Observable } from "rxjs";

const observable = new Observable(function subscribe(subscriber) {
  // Keep track of the interval resource
  const intervalId = setInterval(() => {
    subscriber.next("hello world");
  }, 1000);

  // Provide a way of canceling and disposing the interval resource
  return function unsubscribe() {
    clearInterval(intervalId);
  };
});

const subscription = observable.subscribe(x => console.log(x));
subscription.unsubscribe();
```
</details>