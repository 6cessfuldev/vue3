<template>
	<div>
	<div class="name">{{ name }}</div>
	<input type="text" v-bind:value="name"> 
	<button 
		class="btn btn-primary"
		v-on:click="consoleLog">
		Click
	</button>
	</div>
</template>

<script>
import { ref } from 'vue' ;
	
export default {
	setup() {
		const name = ref('Kossie Coder');
		
		const myName = "Yuk"
		
		const greeting = (name) => {
			return 'Hello, ' + name;
		}
		
		const consoleLog = () => {
			name.value = name.value + '1';
		};
		
		return {
			name,
			myName,
			greeting,
			consoleLog,
		};
	}
}
</script>

<style></style>