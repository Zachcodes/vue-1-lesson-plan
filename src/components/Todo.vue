<template>
    <div class="todo-main-container">
        <!-- Step 2 -->
        <div>{{listTitle}}</div>
        <!-- Step 1 -->
        <ul v-if="list.length">
            <li v-for="(item, i) in list">
                 <!-- Step 8 (add delete item) -->
                {{item}} <button v-on:click="deleteItem(id, i)">Delete Item</button>
            </li>
        </ul>
        <!-- Step 9 (add v-else and v-if) -->
        <div v-else>No items currently</div>
        <!-- Step 4 -->
        <!-- New Item: <input v-model="newItem" v-on:keyup.enter="addItem"/> <button v-on:click="addItem">Add list item</button> -->
        <!-- Step 7 (Alter this v-on:keyup and v-on:click to call a method passed from the parent) -->
        New Item: <input v-model="newItem" v-on:keyup.enter="addItem"/> <button v-on:click="addItem">Add list item</button>
    </div>
</template>

<script>
export default {
    name: 'todo',
    // Step 2 
    // props: ['listTitle'],
    // Step 5
    props: ['listTitle', 'list', 'id', 'addItemToList', 'deleteItem'],
    data() {
        return {
            // Step 5
            // list: ['Get groceries', 'Registration', 'Finish book'],
            newItem: ''
        }
    },
    methods: {
        // Step 7 (update function)
        addItem() {
            if(this.newItem.length) {
              this.addItemToList(this.id, this.newItem)
              this.newItem = ''
            } 

        }
    }
}
</script>

<style scoped>
/* Step 3 */
.todo-main-container {
    width: 300px;
    border: 1px solid black;
    margin: 5px;
}
</style>