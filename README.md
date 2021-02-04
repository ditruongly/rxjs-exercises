# Exercise 1

```javascript
document.addEventListener('click', () => console.log('Clicked!'));
```

<details>
<summary>Solution</summary>

```javascript
import { fromEvent } from 'rxjs';

fromEvent(document, 'click').subscribe(() => console.log('Clicked!'));
```
</details>
