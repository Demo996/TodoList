<template>
    <li @mouseenter="enterShow(true)" @mouseleave="enterShow(false)" :style="{'background-color':bgcl}">
        <input type="checkbox" v-model="todo.complete">{{todo.title}}
        <button v-show="isEnter" @click="deleteRow">删除</button>
    </li>
</template>
<script>
    export default {
        props: {
            todo: Object,
            index: Number,
            deleteItem: Function
        },
        data() {
            return {
                bgcl: "",
                isEnter: false
            }
        },
        methods: {
            enterShow(isEnter) {
                if (isEnter) {
                    this.bgcl = "#CCC"
                    this.isEnter = true
                } else {
                    this.bgcl = ""
                    this.isEnter = false
                }
            },
            deleteRow() {
                const {
                    index,
                    deleteItem
                } = this
                deleteItem(index)
            }
        }
    }
</script>
<style scoped>
    button {
        float: right;
        outline: none;
        width: 100px;
        height: 30px;
        background-color: cadetblue;
        border-radius: 5px;
    }
</style>