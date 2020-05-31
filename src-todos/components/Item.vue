<template>
    <li @mouseenter="liNode(true)" @mouseleave="liNode(false)" :class="myClass">
     <label>
         <input type="checkbox" v-model="isCheck"/>
        <span>{{todo.content}}</span>
    </label>
     <button class="btn btn-danger" v-show="isShow" @click="delT">删除</button>
 </li>
</template>

<script type="text/ecmascript-6">
export default {
    props:['todo','delOne','index','updataOne'],
    computed:{
        isCheck:{
            get(){
                return this.todo.isOver
            },set(val){
                this.updataOne(this.index,val)
            }
        }
    },
    data(){
        return{
            isShow:false,
            myClass:'classB'
        }
    },
    methods:{
        liNode(flag){
            if(flag){
                this.isShow = true
                this.myClass='classA'
            }else{
                this.isShow = false
                this.myClass='classB'
            }
        },
        delT(index){
            this.delOne(this.index)
        }
    }
}
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
.classA{
    background-color: #aaaaaa;
}
.classB{
    background-color: #ffffff;
}
</style>
