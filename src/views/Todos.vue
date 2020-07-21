<template>
  <div>
    <h2>ToDo list</h2>
    <add-item
      @create-item="createItem"
    />
    <hr>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <hr>
    <Loader v-if="loading"/>
    <todo-list
      v-else-if="filterItems.length"
      :items="filterItems"
      @delete-item="deleteItem"
      @check-item="checkItem"
    />
    <p v-else>No Todos!</p>
    <hr>
    <router-link to="/">Home</router-link>
  </div>
</template>

<script>
	import TodoList from "../components/TodoList";
	import AddItem from "../components/AddItem";
	import Loader from "../components/Loader";

	export default {
		name: 'app',
		data: () => ({
			items: [],
      loading: true,
      filter: 'all'
		}),
		mounted() {
			fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json => {
				setTimeout(() => {
					this.loading = false;
					this.items = json
				}, 1500)
			})
    },
		components: {
			TodoList,
			AddItem,
      Loader
		},
    computed: {
			filterItems() {
        if (this.filter === 'all') {
					return this.items
				}
        if (this.filter === 'completed') {
        	return this.items.filter(i => i.completed)
        }
        if (this.filter === 'not-completed') {
        	return this.items.filter(i => !i.completed)
        }
      }
    },
		methods: {
			deleteItem(id) {
				this.items = this.items.filter(item => id !== item.id)
			},
			createItem(title) {
				const item = {
					id: + new Date(),
					title,
					completed: false
				};
				this.items.push(item)
			},
      checkItem(id) {
				const item = this.items.find(item => id === item.id);
        item.completed = !item.completed;
        this.items = [...this.items];
      }
		}
	}
</script>
