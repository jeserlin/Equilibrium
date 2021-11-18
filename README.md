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

(b) How to fix this function so answer is [0,1,2,3,4]


2. Consider the following code (10)

```javascript
const aObject = {a: 1, b: 2}
const bObject = aObject
bObject.a = 999
```

(a) `aObject` after line 3 is

(b) make `cObject` which the value is a clone of `aObject`, and `cObject` is not reference to `aObject` or `bObject`


3. Write a function it will output this (10)
Greet('Hello')('John') ⇒ 'Hello John'
Greet('Hi')('Dennis') ⇒ 'Hi Dennis'


4. Name all life-cycles for React Component (5)


5. list 5 functional component hooks, which one interests you most, why (10)


6. Consider the following Component (20)
```jsx
const ButtonCounter = () => {

	const [count, setCount] = useState();
  const handleClick = useCallback(() => {
    setCount(count+1)
  }, []);

  return (
    <button
      onClick={handleClick}
    >
      {count}
    </button>
  )
}
```
Explain what this function does. If you find any problem, state it and fix the component 


7. Implement this Component (25)
Each second, increase counter value by one. You can use class component or functional component
```javascript
<div>{counter}</div>
```

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




