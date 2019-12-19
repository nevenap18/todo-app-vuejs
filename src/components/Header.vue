<template>
  <div class="gradient-header">
      <h1>ToDo app</h1>
      <p :class="{hidden: count===0}">done: {{doneCount}}/{{count}}</p>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: ["count", "doneCount"]
}
</script>

<style lang="scss" scoped>
@import "@/styles/_variables.scss";

.gradient-header {
  height: 15%;
  width: 500px;
  background-image: linear-gradient(-90deg, $darkBlue, $lightBlue);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 10px 10px 0 0;
  position: relative;

    h1 {
      color: $grayOne;
      font: {
          size: 35px;
          weight: 700;
      }
    }
    p{
      color: $grayOne;
      position: absolute;
      right: 10px;
      bottom: -5px; 
    }
    .hidden {
      visibility: hidden;
    }
}
</style>
