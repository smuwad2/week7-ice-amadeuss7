<script>
export default {
// Add code in appropriate places
    data() {
            return {
                items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
                newItem: ''
            }
            
        },
        methods: {
            addItem() {
                if (this.newItem && this.newItem.trim()) {
                    this.items.push(this.newItem.trim());
                    this.newItem = '';
                }
            },
            deleteItem(idx) {
                this.items.splice(idx, 1);
            }
        }
    }
</script>

<template>

    <h2>Shopping Cart</h2>
    <input v-model="newItem" placeholder="Add item">
    <button @click="addItem">add</button>
    <ul>
        <li v-for="(item, idx) in items" :key="item" role="listitem">
            {{ item }} <button @click="deleteItem(idx)">delete</button>
        </li>
    </ul>
   
</template>
