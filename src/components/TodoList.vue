<template>
    <ul>
        <li v-for="(item, i) in items" :key="i">
            <TodoItem :item="item" />
            <button class="deleteItem" @click="deleteItem(i)">delete</button>
        </li>
    </ul>
</template>

<script>
import TodoItem from './TodoItem'

export default {
    props: {
        items: {
            type: Array,
            required: true
        }
    },
    components: {
        TodoItem
    },
    methods: {
        deleteItem(id) {
            this.$emit('delete-item', id)
        }
    }
}
</script>

<style scoped>
.deleteItem {
    border: none;
    background-color: rgb(247, 96, 126);
    border-radius: 5px;
    color: white;
    padding: 3px;
}
li {
    text-align: left;
    list-style-type: none;
    border: 2px dotted black;
}
</style>