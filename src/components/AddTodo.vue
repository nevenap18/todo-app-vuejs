<template>
  <div id="addTodo">
    <input class="add-task" v-model="task" @keyup.enter="addTask" type="text" name="title" placeholder="Enter a task...">
    <button value="Submit" @click="addTask" class="add-button">+</button>
  </div>
</template>

<script>
export default {
  name: 'AddTodo',
  props: ["todos"],
  data(){
    return {
      task: ''
    }
  },
  methods: {
    addTask(){
      if(this.task===''){
        return
      }
      this.$emit('addTask', this.task)
      this.task= ''
    }
  }
}
</script>

<style lang="scss" scoped>
@import "@/styles/_variables.scss";

#addTodo {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  background-color:  $grayTwo;
  padding: 10px;
}
.add-task {
  border: 2px solid $gray;
  border-radius: 10px;
  padding: 5px 15px;
  background: $grayOne;
  margin: 0px 10px;
  height: 20px;
  width: 250px;
  outline: none;
}
.add-button{
  border-radius: 50%;
  background: $lightBlue;
  color: $grayOne;
  border: none;
  padding: 5px;
  cursor: pointer;
  width: 25px;
  height: 25px;
  box-shadow: 0 0 5px $lightestBlue;
  font-style: bold;
  outline: none;

  &:hover {
    background: $lightestBlue;
    width: 27px;
    height: 27px;
  }
}
</style>
