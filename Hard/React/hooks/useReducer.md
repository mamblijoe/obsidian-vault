`useReducer` — это `React Hook`, который позволяет работать со стейтом в `redux` стиле.

>[!success] В `dev` режиме вызывается дважды

Для использования колбека в качестве начального значения нужно передавать его, а не вызывать

```jsx
// Плохо
function createInitialState(username) {  
// ...  
}  

function TodoList({ username }) {  
	const [state, dispatch] = useReducer(reducer, createInitialState(username));  
// ...
// ...
// Хорошо

function createInitialState(username) {  
// ...  
}  

function TodoList({ username }) {  
	const [state, dispatch] = useReducer(reducer, username, createInitialState);  
// ...
// ...
```