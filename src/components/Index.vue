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
                //事项列表从浏览器数据库中获取
                todoList: JSON.parse(window.localStorage.getItem("todo_ist") || '[]')
            }
        },
        methods: {
            //删除当前事项
            deleteItem(index) {
                this.todoList.splice(index, 1)
            },
            //全选或者全不选
            selectAllItems(checked) {
                this.todoList.forEach(el => {
                    el.complete = checked
                });
            },
            //删除已完成事项
            deleteCompItems() {
                this.todoList = this.todoList.filter((item) => !item.complete)
            }
        },
        watch: {
            //监听事项列表的变化，然后实时存进浏览器中，以便下次打开浏览器能直接加载上次的列表数据
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