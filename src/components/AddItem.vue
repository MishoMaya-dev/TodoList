<template>
  <div>
    <input type="text" v-model="title">
    <button @click="createItem">Create item</button>
  </div>
</template>

<script>
	export default {
		name: "AddItem",
    data: () => ({
      title: ''
    }),
    methods: {
			createItem() {
				this.$emit('create-item', this.title);
				this.title = '';
      }
    }
	}
</script>

<style scoped>
  div {
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
    margin-bottom: 20px;
  }
  input {
    width: 70%;
    height: 27px;
  }
  button {
    width: 25%;
    height: 27px;
  }
</style>
