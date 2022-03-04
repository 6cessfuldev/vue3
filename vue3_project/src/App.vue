<template>
	<div class="container">
		<h2>To-Do List</h2>
		<form v-on:submit.prevent="addList">
			<div class="d-flex">
				<div class="flex-frow-1 mr-2">
					<input class="form-control" type="text" v-model="todo" placeholder="Type new to-do"> 
				</div>
				<div>
					<button class="btn btn-primary" type="submit">
						Add
					</button>	
				</div>
			</div>
			
			<div v-show="hasError" style="color: red">
				This field cannnot be empty
			</div>
			
		</form>
		<div class="card mt-2" v-for="todo in todos" :key="todo.id">
			<div class="card-body p-2 d-flex align-items-center">
				<div class="form-check flex-grow-1">
					<input class="form-check-input" type="checkbox" v-model="todo.completed">
					<label class="form-check-label" :class="{todo: todo.completed}">
						{{ todo.subject }}
					</label>
				</div>
				<div>
					<button class="btn btn-danger tn-sm" @click="deleteTodo">
						Delete
					</button>
				</div>
			</div>		
		</div>
	</div>
</template>

<script>
import { ref } from 'vue' ;
	
export default {
	setup() {
		const todo = ref('');
		const todos = ref([]);		
		
		const hasError = ref(false);
		
		const todoStyle = {
			textDecoration: 'line-through',
			color: 'gray'
		}
		
		
		const addList = () => {
			if(todo.value === ''){
				hasError.value = true;
			} else {
				hasError.value = false;
				todos.value.push({
				id: Date.now(),
				subject: todo.value,
				completed: false,
			})
			todo.value="";} 
			
		};
		
		const deleteTodo = () => {
			console.log('delete todo')
		}
		
		return {
			todo,
			todos,
			hasError,
			addList,
			todoStyle,
			deleteTodo,
		};
	}
}
</script>

<style>

	.todo {
		color: gray;
		text-decoration: line-through;
	}
	
</style>