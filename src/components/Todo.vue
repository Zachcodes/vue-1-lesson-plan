<template>
    <!-- <div class="todo-main-container"> -->
        <!-- Optional step after completion -->
    <div v-bind:class="[list.length ? hasItems : noItems, todoMainContainer]">
        <!-- Step 2 -->
        <div>{{listTitle}}</div>
        <!-- Step 1 -->
        <!-- <ul v-if="list.length">
            <li v-for="(item, i) in list"> -->
                 <!-- Step 8 (add delete item) -->
                <!-- {{item}} <button v-on:click="deleteItem(id, i)">Delete Item</button>
            </li>
        </ul> -->
        <!-- Optional step here for if finish early -->
        <ul v-if="list.length">
            <transition-group name="list-transition">
                <li v-for="(item, i) in list" v-bind:key="item">
                    <!-- Step 8 (add delete item) -->
                    {{item}} <button v-on:click="deleteItem(id, i)">Delete Item</button>
                </li>
            </transition-group>
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
    name: 'Todo',
    // Step 2 
    // props: ['listTitle'],
    // Step 5
    props: ['listTitle', 'list', 'id', 'addItemToList', 'deleteItem'],
    data() {
        return {
            // Step 5
            // list: ['Get groceries', 'Registration', 'Finish book'],
            newItem: '',
            hasItems: 'has-items',
            noItems: 'no-items',
            todoMainContainer: 'todo-main-container'
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
.has-items {
    box-shadow: 3px 3px 3px green;
}
.no-items {
    box-shadow: 3px 3px 3px red;
}
/* Add if there is time at the end of the class */
.list-transition-enter-active, .list-transition-leave-active {
  transition: all 1s;
}
.list-transition-enter, .list-transition-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>