# Exercise 3

```javascript
let count = 0;
let rate = 2000;
let lastClick = Date.now() - rate;
document.addEventListener('click', () => {
  if (Date.now() - lastClick >= rate) {
    console.log(`Clicked ${++count} times`);
    lastClick = Date.now();
  }
});
```

<details>
<summary>Solution</summary>

```javascript
fromEvent(document, "click")
  .pipe(
    throttleTime(2000),
    scan(count => count + 1, 0)
  )
  .subscribe(count => console.log(`Clicked ${count} times`));
```
</details>