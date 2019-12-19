<template>
  <div class="item">
    <input type="checkbox" :checked='todo.done' class="checkbox" @change="updateItem" />
    <p :class="{ done: todo.done }">{{todo.title}}</p>
    <button class="del-button" @click="deleteItem">X</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo", "index"],
  methods: {
    updateItem(e) {
      this.$emit("updateItem", this.index, e.target.checked);
    },
    deleteItem() {
      this.$emit("deleteItem", this.index);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "@/styles/_variables.scss";

.item {
  text-align: left;
  padding: 5px 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;

  .checkbox {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 2px solid $gray;
    -webkit-appearance: none;
    outline: none;
    cursor: pointer;
    background-color: $grayOne;

    &:hover {
      border: 3px solid $gray;
    }
    &:checked {
      background-color: $lightBlue;
      box-shadow: inset 0 0 0 2px $grayOne;
    }
  }

  p {
    font-size: 17px;
    color: $darkBlue;
    width: 80%;
  }
  &:hover .del-button {
    visibility: visible;
  }
  .done {
    text-decoration: line-through;
    color: $grayThree;
  }
  .del-button {
    visibility: hidden;
    width: 20px;
    height: 20px;
    background: transparent;
    border: none;
    outline: none;
    text-align: center;
    color: $grayThree;
    cursor: pointer;

    font: {
      weight: 700;
      size: 17px;
    }
    &:hover {
      color: $redDelete;
    }
  }
}
</style>
