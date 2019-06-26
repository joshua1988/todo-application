<template>
  <div>
    <button v-on:click="clearItems">
      clear all
    </button>
  </div>
</template>

<script>
export default {
	methods: {
		clearItems: function() {
			this.$emit('clear');
		},
	},
};
</script>

<style>
</style>
