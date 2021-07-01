<template>
<div class="box">
    <TodoHeader :todo="todoList"/>
    <TodoList :todo="todoList" :deleteItem="deleteItem"/>
    <TodoFooter :todo="todoList" :selectAllItems="selectAllItems" :deleteCompItems="deleteCompItems"/>
</div>
</template>
<script>
    import TodoHeader from "./TodoHeader.vue"
    import TodoList from "./todoList.vue"
    import TodoFooter from "./TodoFooter.vue"
    export default {
        components: {
            TodoHeader,
            TodoList,
            TodoFooter
        },
        data() {
            return {
                todoList: JSON.parse(window.localStorage.getItem("todo_ist") || '[]')
            }
        },
        methods: {
            deleteItem(index) {
                this.todoList.splice(index, 1)
            },
            selectAllItems(checked) {
                this.todoList.forEach(el => {
                    el.complete = checked
                });
            },
            deleteCompItems() {
                this.todoList = this.todoList.filter((item) => !item.complete)
            }
        },
        watch: {
            todoList: {
                deep: true,
                handler(newVal) {
                    window.localStorage.setItem("todo_ist", JSON.stringify(newVal))
                }
            }
        }
    }
</script>
<style scoped>
    * {
        box-sizing: border-box;
    }
    
    .box {
        width: 500px;
        height: auto;
        border: 1px solid gray;
        padding: 5px;
    }
</style>