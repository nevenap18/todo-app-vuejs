<template>
  <div class="todos">
      <div v-for="(todo, index) in todos" :key="todo.id" >
        <TodoItem :todo="todo" :index="index" @deleteItem="deleteItem" @updateItem="updateItem"/>
      </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'Todos',
  components: {
      TodoItem
  },
  props: ["todos", "doneCount"],
  methods: {
    deleteItem(index){
      this.$emit('deleteItem', index)
    },
    updateItem(index, done){
      this.$emit('updateItem', index, done)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "@/styles/_variables.scss";

.todos {
  width: 100%;
  height: 85%;
  overflow: auto;
  border-radius: $radius;
}
</style>
