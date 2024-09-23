`useState` — это хук, который позволяет вам добавить и управлять состоянием в компоненте.

>[!success] В `dev` режиме функция  `initializer` вызывается дважды

Для использования колбека в качестве начального значения нужно передавать его, а не вызывать

```jsx
// Плохо
function TodoList() {  
	const [todos, setTodos] = useState(createInitialTodos());  
// ...
// Хорошо
function TodoList() {  
	const [todos, setTodos] = useState(createInitialTodos);  
// ...
```

>[!tip] Стейт сбрасывается если `key`  компонента изменился

