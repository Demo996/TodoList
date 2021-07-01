<template>
<div style="width: 100%;">
    <input v-model="title" type="text" @keyup.enter="addItem" placeholder="请输入你的任务名称，按回车键确认"/>
</div>
</template>
<script>
    export default {
        props: {
            todo: Array
        },
        data() {
            return {
                title: ""
            }
        },
        methods: {
            addItem() {
                const {
                    title,
                    todo
                } = this
                let obj = {
                    title,
                    complete: false
                }
                todo.unshift(obj)
                this.title = ""
            }
        }
    }
</script>
<style scoped>
    * {
        box-sizing: border-box;
    }
    
    input {
        width: 100%;
        border-radius: 5px;
        height: 30px;
        border-width: 1px;
        border-color: #ccc;
        padding: 5px;
        outline: none;
    }
</style>