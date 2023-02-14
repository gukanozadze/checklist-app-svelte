<script>
	import { todos } from '../../store/TodoStore'
	import TodoInput from './TodoInput.svelte'
</script>

<section class="soace-y-4 mt-8">
	{#each $todos as todo (todo.id)}
		<TodoInput {todo} />
	{/each}
</section>
