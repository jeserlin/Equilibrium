# Equilibrium

1. Consider the following code (10)

```javascript
var answer = []
for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    answer.push(i)
  }, i)
}
```

(a) What is the answer?

Ans:
The `answer` will be as below in every milisecond:
- []
- [5]
- [5, 5]
- [5, 5, 5]
- [5, 5, 5, 5]
- [5, 5, 5, 5, 5]

(b) How to fix this function so answer is [0,1,2,3,4]

Ans:
```javascript
var answer = []
for(var i = 0; i<5; i++) {
  setTimeout(((i) => {
    answer.push(i)
  })(i), i)
}
```

* * *

2. Consider the following code (10)
```javascript
const aObject = {a: 1, b: 2}
const bObject = aObject
bObject.a = 999
```

(a) `aObject` after line 3 is

Ans: `aObject` is `{ a: 999, b: 2 }`.

(b) make `cObject` which the value is a clone of `aObject`, and `cObject` is not reference to `aObject` or `bObject`

Ans:
```javascript
const cObject = Object.assign({}, aObject);
```

* * *

3. Write a function it will output this (10)
Greet('Hello')('John') ⇒ 'Hello John'
Greet('Hi')('Dennis') ⇒ 'Hi Dennis'

Ans:
```javascript
const Greet = (greeting) => {
  return (name) => {
    console.log(`${greeting} ${name}`)
  };
}
```

* * *

4. Name all life-cycles for React Component (5)

Ans: Mounting, Updating, and Unmounting.

* * *

5. list 5 functional component hooks, which one interests you most, why (10)

Ans: 
functional component hooks:
- useState
- useEffect
- useCallback
- useRef
- useContext

`useEffect` interests the most, because before having `useEffect`, we need to deal with `componentDidMount`, `componentDidUpdate` and `componentWillUnmount`. It's earier to understand and reduce the complexity of the development.

* * *

6. Consider the following Component (20)
```jsx
const ButtonCounter = () => {

  const [count, setCount] = useState();

  const handleClick = useCallback(() => {
    setCount(count+1)
  }, []);

  return (
    <button onClick={handleClick}>
      {count}
    </button>
  )
}
```
Explain what this function does. If you find any problem, state it and fix the component.

Ans:
When user clicks on the button, the couter will increase `1` each time.
```jsx
const ButtonCounter = () => {

  const [count, setCount] = useState(0); // should have default value
  const handleClick = useCallback(() => {
    setCount((prevCount) => prevCount+1) // should update count with previous state
  }, []);

  return (
    <button onClick={handleClick}>
      {count}
    </button>
  )
}
```

* * *

7. Implement this Component (25)
Each second, increase counter value by one. You can use class component or functional component
```javascript
<div>{counter}</div>
```
Ans:
```javascript
const Counter = () => {
  const [counter, setCounter] = useState(0);

  useEffect(() => {
    const increaseCounter = setInterval(() => {
      setCounter(prevCounter => prevCounter + 1);
    }, 1000);

    return () => clearInterval(increaseCounter);
  }, []);

  return (
    <div>{counter}</div>
  );
};
```

* * *

8. Consider the following Component (10)
```jsx
const Child = ({
  name,
  friendCount
}) => {
  return (
    <div>
      <div>
        {name}
      </div>
      <div>
        {friendCount}
      </div>
    </div>
  )
}
```
Make `Child` component only re-render when `name` prop value changes.

Ans:
```javascript
const isNameEqual = (prevProps, nextProps) => prevProps.name === nextProps.name;
const Child = ({
  name,
  friendCount
}) => {
  return (
    <div>
      <div>
        {name}
      </div>
      <div>
        {friendCount}
      </div>
    </div>
  )
};

export default React.memo(Child, isNameEqual);
```
