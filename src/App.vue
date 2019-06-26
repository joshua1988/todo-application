<template>
  <div>
    <todo-header></todo-header>
    <todo-input
			v-on:add="addTodoItem"
		></todo-input>
    <todo-list
			v-bind:todolist="todoItems"
			v-on:remove="removeTodoItem"
		></todo-list>
    <todo-footer
			v-on:clear="removeAllItems"
		></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
	components: {
		// '컴포넌트 이름': 컴포넌트 내용,
		'todo-header': TodoHeader,
		'todo-input': TodoInput,
		'todo-list': TodoList,
		'todo-footer': TodoFooter,
	},
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		fetchTodoItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				var item = localStorage.key(i);
				this.todoItems.push(item);
			}
		},
		addTodoItem: function(value) {
			// 배열에 추가
			this.todoItems.push(value);
			// 저장소에 저장
			localStorage.setItem(value, value);
		},
		removeTodoItem: function(todo, index) {
			// 배열에서 삭제
			this.todoItems.splice(index, 1);
			// 저장소에서 삭제
			localStorage.removeItem(todo);
		},
		removeAllItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	// 컴포넌트가 생성되자마자 실행되는 로직
	created: function() {
		this.fetchTodoItems();
	},
};
</script>

<style>
</style>
