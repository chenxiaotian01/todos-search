<template>
    <ul class="todo-main">
        <item v-for="(todo, index) in todos" :key="todo.id" 
        :todo="todo"
        :delOne="delOne"
        :index="index"
        :updataOne="updataOne"
        ></item>
    </ul>
</template>

<script type="text/ecmascript-6">
import Item from '@/components/Item'
export default {
    components:{
        Item
    },
    props:{
        todos:Array,
        delOne:Function,
        updataOne:Function
    }
}
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}

</style>
