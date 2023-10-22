<script>
	import { onMount } from 'svelte';
	import ToDoControls from './ToDoControls.svelte';
	import ToDoItem from './ToDoItem.svelte';

	let items = []
	let id = 0;
  
  onMount(() => {
    if (localStorage.key('items')) {
      items = JSON.parse(localStorage.getItem('items'))
    }
    if (items.length) {
		items.forEach((i) => {
			if (id < i.id) {
				id = i.id;
			}
		});
		id++;
	}
  })

	function onChangeStatus(event) {
		const item = items.find((i) => i.id === event.detail.id);
		item.isDone = !item.isDone;
		console.log(items);
		items = items;
    localStorage.setItem('items', JSON.stringify(items))
	}

	function addItem(event) {
		const item = {
			id: id++,
			text: event.detail.text,
			isDone: false
		};
		items.push(item);
		items = items;
    localStorage.setItem('items', JSON.stringify(items))
	}

	function deleteItem(event) {
		const idx = items.findIndex((i) => i.id === event.detail.id);
		items.splice(idx, 1);
		items = items;
    localStorage.setItem('items', JSON.stringify(items))
	}
</script>

<div class="todolist">
	<ToDoControls on:add={addItem} />
	<div class="todolist__field">
		{#each items as item}
			<ToDoItem
				id={item.id}
				text={item.text}
				isDone={item.isDone}
				on:change={onChangeStatus}
				on:delete={deleteItem}
			/>
		{/each}
	</div>
</div>

<style>
	.todolist {
		max-width: 634px;
		max-height: 797px;
		width: 100%;
		height: 100%;
		padding: 44px 60px;
		background: #e6e6e6;
		border-radius: 15px;
		display: flex;
		flex-direction: column;
		gap: 22px;
	}

	.todolist__field {
		flex-grow: 1;
		background: #fff;
		border-radius: 15px;
		padding: 20px;
		overflow-y: auto;
		display: flex;
		flex-direction: column;
		gap: 15px;
	}
</style>
