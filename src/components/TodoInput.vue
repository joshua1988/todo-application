<template>
  <div>
    <input 
			type="text" 
			v-model="inputText"
			v-on:keyup.enter="addTodo">
    <button v-on:click="addTodo">add</button>
  </div>
</template>

<script>
export default {
	data() {
		return {
			inputText: '',
		};
	},
	methods: {
		addTodo: function() {
			var value = this.inputText;
			this.$emit('add', value);
			// localStorage.setItem(value, value);
			this.clearInput();
		},
		clearInput: function() {
			this.inputText = '';
		},
	},
};
</script>

<style>
</style>
