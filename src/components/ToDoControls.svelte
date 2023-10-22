<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	let inputValue = '';
	function onClick() {
		if (inputValue.length) {
      dispatch('add', { text: inputValue })
      inputValue = ''
		}
	}

</script>

<div class="todo-controls">
	<input class="todocontrols__input" type="text" bind:value={ inputValue } />
	<button class="todo-controls__add" on:click={onClick}>Add</button>
</div>

<style>
	.todo-controls {
		display: grid;
		grid-template-columns: 2.25fr 1fr;
		max-height: 60px;
		height: 100%;
		font-size: 18px;
	}
	.todocontrols__input {
		outline: none;
		border: none;
		padding: 20px;
		border-radius: 10px 0px 0px 10px;
		background: #fff;
		font-size: inherit;
	}
	.todo-controls__add {
		outline: none;
		border: none;
		border-radius: 0px 10px 10px 0px;
		background: #fbcc28;
		cursor: pointer;
		font-size: inherit;
	}
</style>
