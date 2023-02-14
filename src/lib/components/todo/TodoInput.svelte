<script>
	import { deleteTodo, toggleComplete, editTodo } from '../../store/TodoStore'

	export let todo

	$: completeClass = todo.complete ? 'bg-green-three' : 'bg-leaf-one'
</script>

<div class="flex items-center justify-between rounded-md border-2 border-gray-one px-5 py-4">
	<div class="flex w-full max-w-lg items-center justify-start">
		<label for={`${todo.id}-checkbox`} class="sr-only">Complete Todo</label>
		<input
			id={`${todo.id}-checkbox`}
			type="checkbox"
			checked={todo.complete}
			on:change={() => toggleComplete(todo.id)}
			class="focus:outline-offeset-2 h-4 w-4 rounded border border-gray-three bg-cream-four 
            text-green-four focus:border-green-five focus:outline focus:outline-2 focus:outline-green-five"
		/>
		<label for={`${todo.id}-text`} class="sr-only">EditTodo</label>
		<input
			id={`${todo.id}-text`}
			type="text"
			placeholder="Enter a todo"
			on:input={(e) => editTodo(todo.id, e.target.value)}
			value={todo.text}
			class="focus:ouline-none ml-5 flex-1 text-ellipsis rounded-none border-x-0
             border-t-0 border-b border-dashed border-b-gray-two bg-cream-four
              px-0 pb-1 text-base font-normal text-gray-three placeholder:text-gray-two
            focus:border-gray-three focus:ring-0"
		/>

		<span
			class="{completeClass} ml-5 hidden rounded-full py-0.5 px-2 text-sm font-normal text-gray-five md:block"
		>
			{todo.complete ? 'Complete' : 'In Progress'}
		</span>
	</div>
	<button type="button" on:click={() => deleteTodo(todo.id)}>Delete</button>
</div>
