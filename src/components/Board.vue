<template>
  <div class="Board">
    <AddTask />
  </div>
</template>

<script>
import AddTask from "./AddTask";
export default {
  name: "Board",
  components: {
    AddTask,
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


