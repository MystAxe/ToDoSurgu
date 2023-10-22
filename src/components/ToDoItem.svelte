<script>
  export let id;
  export let text;
  export let isDone;
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher()
  
  function onDelete() {
    
  }
</script>

<div class="todo-item" class:todo-item_done={isDone}>
	<input
		class="todo-item__checkbox"
		type="checkbox"
		value=""
		aria-label="..."
    on:change={dispatch('change', { id })}
    checked={isDone}
	/>
	<div class="todo-item__text">{text}</div>
	<button class="todo-item__delete" on:click={dispatch('delete', { id })}>
		<img class="todo-item__del-img" src="images/trash.svg" alt="" />
	</button>
</div>

<style>
	.todo-item {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 15px;
    padding: 26px 20px;
    background: #FFEBEB;
    border-radius: 10px;
	}

  .todo-item_done {
    background: #EBFFED;
  }

  .todo-item_done .todo-item__text {
    text-decoration: line-through;
  }

	.todo-item__checkbox {
		width: 24px;
		height: 24px;
	}

	.todo-item__text {
		flex: 1;
    line-height: 1;
	}

	.todo-item__delete {
		border: none;
		background: none;
		cursor: pointer;
	}
</style>
