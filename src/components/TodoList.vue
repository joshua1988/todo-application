<template>
  <div>
		<transition-group tag="ul" name="todo">
    <!-- <ul> -->
      <li v-for="(todoItem, index) in todolist"
				v-bind:key="index">
        <span>{{ todoItem }}</span>
        <button 
          v-on:click="removeTodoItem(todoItem, index)">remove</button>
      </li>
    <!-- </ul> -->
		</transition-group>
  </div>
</template>

<script>
export default {
	props: ['todolist'],
	// data() {
	// 	return {
	// 		todoItems: [],
	// 	};
	// },
	methods: {
		// fetchTodoItems: function() {
		// 	// 브라우저 저장소의 데이터를 불러오기
		// 	for (var i = 0; i < localStorage.length; i++) {
		// 		var item = localStorage.key(i);
		// 		this.todoItems.push(item);
		// 	}
		// 	// 서버의 데이터 불러오기
		// 	// axios.get();
		// },
		removeTodoItem: function(todo, index) {
			console.log('deleted', todo, index);
			this.$emit('remove', todo, index);

			// arr.splice('시작할 배열 인덱스', '갯수');
			// this.todoItems.splice(index, 1);
			// // 브라우저 저장소의 데이터 삭제
			// localStorage.removeItem(todo);
			// 서버의 데이터를 삭제
			// axios.delete();
		},
	},
	// // 컴포넌트가 생성되자마자 실행되는 로직
	// created: function() {
	// 	this.fetchTodoItems();
	// },
};
</script>

<style>
.todo-enter-active,
.todo-leave-active {
	transition: all 1s;
}
.todo-enter, .todo-leave-to /* .list-leave-active below version 2.1.8 */ {
	opacity: 0;
	transform: translateY(30px);
}
</style>
