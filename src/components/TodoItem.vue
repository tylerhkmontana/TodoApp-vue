<template>
    <label :class="checked">
        <input @change="isChecked = !isChecked" type="checkbox">
        {{ item }}
    </label>
</template>

<script>
export default {
    props: {
        item: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            isChecked: false
        }
    },
    methods: {
        deleteItem(id) {
            this.$emit('delete-item', id)
        }
    },
    computed: {
        checked() {
            if (this.isChecked) {
                return {
                    checked: true
                }
            } else {
                return {
                    checked: false
                }
            }
        }
    }
}
</script>

<style scoped>
.checked {
    text-decoration: line-through black;
}

input[type="checkbox"] {
    vertical-align: middle;
}
</style>