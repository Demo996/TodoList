<template>
<div style="width: 100%;height: 30px;" class="clear">
    <div class="total">
        <input type="checkbox" v-model="isAllSelected">已完成{{completeSize}} / 全部{{todo.length}}
    </div>
    <button class="allClear" v-show="completeSize" @click="deleteCompItems">清除已完成任务</button>
</div>
</template>
<script>
    export default {
        props: {
            todo: Array,
            selectAllItems: Function,
            deleteCompItems: Function
        },
        data() {
            return {}
        },
        methods: {},
        computed: {
            completeSize() {
                return this.todo.reduce((preTotal, item) => preTotal + (item.complete ? 1 : 0), 0)
            },
            isAllSelected: {
                get() {
                    return this.todo.length === this.completeSize && this.todo.length
                },
                set(check) {
                    this.selectAllItems(check)
                }
            }
        }
    }
</script>
<style scoped>
    .clearfix:after {
        content: ".";
        display: block;
        clear: both;
        visibility: hidden;
        line-height: 0;
        height: 0;
    }
    
    .total {
        float: left;
        width: 200px;
        height: 30px;
        text-align: left;
    }
    
    .allClear {
        float: right;
        width: 120px;
        height: 30px;
        outline: none;
        background-color: orange;
        border-radius: 5px;
    }
</style>