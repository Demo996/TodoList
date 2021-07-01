<template>
    <ul class="clearfix">
        <TodoItem v-for="(item,index) in todo" :key="index" :todo="item" :index="index" :deleteItem="deleteItem"/>
    </ul>
</template>
<script>
import TodoItem from "./TodoItem.vue"
export default {
    components: { TodoItem },
    props: {
        todo: Array,
        deleteItem: Function
    },
    data() {
        return{}
    },
    methods: {
    }
}
</script>
<style scoped>
ul {
    width: 100%;
    height: auto;
    list-style: none;
    padding: 0;
    margin: 0;
    margin: 20px 0;
    border: 1px solid #ccc;
}
li {
    height: 30px;
    line-height: 30px;
    font-size: 16px;
    text-align: left;
    list-style: none;
    width: 100%;
    border-bottom: 1px solid #ccc;
}
.clearfix:after {
    content: ".";
    display: block;
    clear: both;
    visibility: hidden;
    line-height: 0;
    height: 0;
}
</style>