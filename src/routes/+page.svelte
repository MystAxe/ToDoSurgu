<script>
	import ToDoApp from '../components/ToDoApp.svelte';
</script>

<main class="todolist__wrapper">
	<ToDoApp />
</main>

<style>
  :global(html) {
  box-sizing: border-box;
}

:global(*,
*::after,
*::before) {
  box-sizing: inherit;
}

:global(ul,
ol) {
  padding: 0;
}

:global(body,
h1,
h2,
h3,
h4,
h5,
h6,
p,
ul,
ol,
li,
figure,
figcaption,
blockquote,
dl,
dd) {
  margin: 0;
}

:global(ol) {
  list-style: none;
}

:global(img) {
  max-width: 100%;
  display: block;
}

:global(input,
button,
textarea,
select) {
  font: inherit;
}

:global(body) {
  font-family: 'Inter', sans-serif;
  font-size: 18px;
  font-weight: 400;
}

	.todolist__wrapper {
		height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 22px;
	}
</style>
