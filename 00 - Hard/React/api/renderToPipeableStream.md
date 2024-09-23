`renderToPipeableStream` рендерит React дерево в `pipeable Node.js Stream`. Затем нужно гидрировать с помощью [[hydrateRoot]]

>[!warning] Этот API специфичен для Node.js. 
>Среды с веб-стримами, такие как `Deno` и современные среды выполнения `Edge`, должны использовать вместо этого `renderToReadableStream`.

## `shell`

Часть приложения вне любых `<Suspense>` называется `shell`

```jsx
function ProfilePage() {  
	return (  
		<ProfileLayout>  
			<ProfileCover />  
			<Suspense fallback={<BigSpinner />}>  
				<Sidebar>  
					<Friends />  
					<Photos />  
				</Sidebar>  
				<Suspense fallback={<PostsGlimmer />}>  
					<Posts />  
				</Suspense>  
			</Suspense>  
			</ProfileLayout>  
	);  
}
```

