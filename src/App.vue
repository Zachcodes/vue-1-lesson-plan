<template>
  <div id="app">
    <!-- Step 10 (bring in time of day using computer property) && Step 11 (Show computed using greeting)-->
    {{greeting}} {{timeOfDay}}
    <!-- Step 5 -->
    <Todo v-for="list in lists"
    :key="list.id"
    :id="list.id"
    :listTitle="list.listTitle"
    :list="list.items"
    :addItemToList="addItemToList"
    :deleteItem="deleteItem"/>
    <!-- Step 3 -->
    <!-- <div class="todo-main-container">Hello</div> -->
  </div>
</template>

<script>
import Todo from './components/Todo.vue'

export default {
  name: 'app',
  components: {
    Todo
  },
  // Step 10 (Show off lifecycle methods with this.timeIntervalId)
  mounted() {
    this.timeIntervalId = setInterval(() => this.timeOfDay = new Date().toLocaleString(), 1000)
  },
  data() {
    return {
      // Step 5
      lists: [
        {
          id: 1,
          items: ['Get groceries', 'Registration', 'Finish book'],
          listTitle: 'My Day'
        },
        {
          id: 2,
          items: ['Salmon', 'Salad', 'Dressing'],
          listTitle: 'Shopping List'
        },
        {
          id: 3,
          items: ['Gift cards', 'Candles', 'Airpods'],
          listTitle: 'Christmas shopping list'
        }
      ],
      // Step 10
      timeIntervalId: 0,
      timeOfDay: new Date().toLocaleString(),
      // Step 11 (add first name)
      firstName: 'Zach'
    }
  },
  methods: {
    // Step 6
    addItemToList(id, newItem) {
      for(let i = 0; i < this.lists.length; i++) {
        if(this.lists[i].id === id) this.lists[i].items.push(newItem)
      }
    },
    // Step 8
    deleteItem(id, itemIndex) {
      for(let i = 0; i < this.lists.length; i++) {
        if(this.lists[i].id === id) this.lists[i].items.splice(itemIndex, 1)
      }
    }
  },
  computed: {
    // Step 11 (bring in computed properties)
    greeting() {
      return `Hello ${this.firstName}, the time and date are`
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5px;
}
</style>
