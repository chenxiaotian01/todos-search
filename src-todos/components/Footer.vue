<template>
<div class="todo-footer">
        <label>
          <input type="checkbox" v-model="isCheckAll"/>
        </label>
        <span>
          <span>已完成{{overNum}}</span> / 全部{{allNum}}
        </span>
        <button class="btn btn-danger" @click="delA">清除已完成任务</button>
      </div>
</template>

<script type="text/ecmascript-6">
export default {
    props:{
        todos:Array,
        updateAll:Function,
        delAll:Function
    },
    computed:{
        overNum(){
            return this.todos.filter(item => item.isOver).length
        },
        allNum(){
            return this.todos.length
        },
        isCheckAll:{
            get(){
                return this.overNum === this.allNum && this.allNum > 0
            },
            set(val){
                this.updateAll(val)
            }
        }
    },
    methods:{
        delA(){
            this.delAll()
        }
    }
}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>
