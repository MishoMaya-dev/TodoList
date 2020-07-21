<template>
  <li>
    <label :class="{'done': item.completed}">
      <input type="checkbox" :checked="item.completed" @input="checkItem">
      <strong>{{ itemIndex + 1 }}</strong>
      {{ item.title }}
    </label>
    <button @click="deleteItem">&#10006</button>
  </li>
</template>

<script>
	export default {
		name: "TodoItem",
    props: {
			item: {
				type: Object,
        required: true
      },
      itemIndex: {
				type: Number,
        required: true
      }
    },
    methods: {
			deleteItem() {
				this.$emit('delete')
      },
      checkItem() {
				this.$emit('check')
      }
    }
	}
</script>

<style scoped>
  li {
    border: 1px solid;
    border-radius: 5px;
    padding: 5px;
    margin: 10px auto;
    display: flex;
    justify-content: space-between;
  }
  label {
    padding: 5px 0;
  }
  input {
    margin-right: 20px;
    transform:scale(1.5);
  }
  button {
    width: 30px;
    height: 30px;
    border: 0;
    border-radius: 50%;
    background-color: #f00;
  }
  .done {
    text-decoration: line-through;
  }

</style>
