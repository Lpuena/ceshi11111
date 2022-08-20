<template>
  <div>
    <div class="todo-container">
      <div class="todo-wrap">
        <my-header :addTodo="addTodo"></my-header>
        <my-list :todos="todos" :checkStatus="checkStatus" :deleteTodo="deleteTodo"></my-list>
        <my-footer :todos="todos"></my-footer>
      </div>
    </div>
  </div>
</template>

<script>
import MyFooter from './components/Footer.vue'
import MyHeader from './components/Header.vue'
import MyList from './components/List.vue'
export default {
  name:'MyApp',
  components:{
    MyFooter,
    MyHeader,
    MyList,
  },
  data() {
    return {
      todos:[
        {id:'01',title:'吃饭',status:true},
        {id:'02',title:'抽烟',status:false},
        {id:'03',title:'喝酒',status:true},
        {id:'04',title:'烫头',status:false},
        {id:'05',title:'开车',status:true}
      ],
    }
  },
  methods: {
    addTodo(todoObj){
      this.todos.unshift(todoObj)
    },
    checkStatus(id){
      this.todos.forEach((todo)=>{
        if(todo.id==id) todo.status=!todo.status
      })
    },
    // 删除一个item项
    deleteTodo(id){
      if(confirm('确定删除吗？')){
        this.todos = this.todos.filter(x=>x.id!==id)
      }
    },
  },
}
</script>

<style>
.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}
.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}
.btn:focus {
  outline: none;
}
.todo-container {
  width: 600px;
  margin: 0 auto;
}
 .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}






</style>