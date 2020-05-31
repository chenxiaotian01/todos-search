<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!-- <Header :addTodo="addTodo"></Header> -->
      <Header ref="add"></Header>
      <Main :todos="todos" :delOne="delOne" :updataOne="updataOne"></Main>
      <Footer :todos="todos" :updateAll="updateAll" :delAll="delAll"></Footer>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import Header from '@/components/Header'
import Main from '@/components/Main'
import Footer from '@/components/Footer'
export default {
    components:{
        Header,
        Main,
        Footer
    },
    mounted(){
        this.$refs.add.$on('addTodo',this.addTodo)
    },
    data(){
        return{
            todos:[
                {id:1,content:"吃饭",isOver:false},
                {id:2,content:"睡觉",isOver:true},
                {id:3,content:"打豆豆",isOver:false}
            ]
        }
    },
    methods:{
        addTodo(obj){
            this.todos.unshift(obj)
        },
        delOne(index){
            this.todos.splice(index,1)
        },
        updataOne(index,val){
            this.todos[index].isOver = val
        },
        updateAll(val){
             this.todos.forEach(item => item.isOver = val)
        },
        delAll(){
            this.todos = this.todos.filter(item => !item.isOver)
        }
    }
}
</script>

<style scoped>
/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

</style>
