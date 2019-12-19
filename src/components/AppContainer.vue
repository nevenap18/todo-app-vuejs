<template>
  <div id="appContainer">
    <Header :count="count" :doneCount="doneCount"/>
    <AddTodo :todos="todos" @addTask="addTask"/>
    <!--<Todos :todos="todos" @deleteItem="deleteItem" @updateItem="updateItem"/> -->
    <div class="todos">
      <div v-for="(todo, index) in todos" :key="todo.id" >
        <TodoItem :todo="todo" :index="index" @deleteItem="deleteItem" @updateItem="updateItem"/>
      </div>
  </div>
  </div>
</template>



<script>
import Header from './Header.vue'
//import Todos from './Todos.vue'
import AddTodo from './AddTodo.vue'
import TodoItem from './TodoItem.vue'

export default {
  name: 'AppContainer',
  components: {
    Header,
    //Todos,
    AddTodo,
    TodoItem
  },
  data() {
    return {
      todos: [],
      count: 0,
      doneCount: 0
    }
  },
  methods: {
    deleteItem(index){
      this.count -= 1
      if (this.todos[index].done){
        this.doneCount -= 1
      }
      this.todos.splice(index, 1)
      localStorage.setItem('todo', JSON.stringify(this.todos))
    },
    addTask(task){
      let id = 0
    
      if (this.todos.length != 0) {
          id = this.todos[this.todos.length - 1].id + 1
      }
      const newTask = {
        title: task,
        done: false,
        id: id
      }
      this.todos.push(newTask)
      localStorage.setItem('todo', JSON.stringify(this.todos))
      this.count += 1
    },
    updateItem(index, done){
      this.todos[index].done = done
      localStorage.setItem('todo', JSON.stringify(this.todos))
      if(done){
        this.doneCount += 1
      } else{
        this.doneCount -= 1
      }
    }
  },
  created(){
    let array = JSON.parse(localStorage.getItem('todo'))
    if(array != undefined){
      this.todos = array
      this.count = this.todos.length
      for (let i = 0; i <= this.todos.length - 1; i++) {
        if (this.todos[i].done) {
            this.doneCount += 1
        }
      } 
    }
  }
}
</script>

<style lang="scss" scoped>
@import "@/styles/_variables.scss";

#appContainer {
  border-radius: $radius;
  display: flex;
  flex-direction: column;
  min-height: 700px;
  height: 75vh;
  width: 500px;
  background-color: $grayTwo;
  box-shadow: 0 0 15px $lightestBlue;
}
::-webkit-scrollbar-track
{
  border-radius: $radius;
  background-color: $grayOne;
}
::-webkit-scrollbar
{
  width: 12px;
  border-radius: $radius;
  background-color: $grayOne;
}
::-webkit-scrollbar-thumb
{
  border-radius: $radius;
  background-color: $gray;
}
.todos {
  width: 100%;
  height: 85%;
  overflow: auto;
  border-radius: $radius;
}
</style>
