<template>
  <div>
    <ul>
      <todo-item
        v-for="(item, i) in items"
        :key="item.id"
        :item="item"
        :item-index="i"
        @delete="$emit('delete-item', item.id)"
        @check="$emit('check-item', item.id)"
      />
    </ul>
  </div>
</template>

<script>
  import TodoItem from './TodoItem'

	export default {
		name: "TodoList",
    props: ['items'],
    components: {
			TodoItem
    },
	}
</script>

<style scoped>
 ul {
   margin: 0 0 20px 0;
   list-style-type: none;
   padding-inline-start: 0;
 }
</style>
