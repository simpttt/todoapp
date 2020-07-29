<template>
  <div class="Board">
    <Task />
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Board",
  components: {
    Task,
  },
};
</script>
<style>
.Board {
  width: 600px;
  height: 1000px;
  background-color: rgb(232, 244, 248);
}
</style>
