<template>
  <div>
    <form @submit.prevent="addTask">
      <input type="text" class="input-todo" v-model="newTask.title" placeholder="Title" />
      <input type="date" class="input-todo" v-model="newTask.due" />
      <button type="submit" class="input-button">Add</button>
    </form>
    <ul v-for="(task,index) in tasks" :key="index" class="tasklist">
      <li>
        <span>{{task.title}} {{task.due}} {{task.status}}</span>
        <span @click="deleteTask(index)" class="delete">×</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      newTask: {
        title: "",
        due: "",
        status: "",
      },
      tasks: [
        {
          title: "aaa",
          due: "dd",
          status: "未了",
        },
      ],
    };
  },
  watch: {
    tasks: {
      handler: function () {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      },
      deep: true,
    },
  },
  mounted: function () {
    this.tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  },
  methods: {
    addTask() {
      this.newTask.status = "未了";
      this.tasks.push(this.newTask);
      this.newTask = {};
    },
    deleteTask(index) {
      if (confirm("are you sure?")) {
        this.tasks.splice(index, 1);
      }
    },
  },
};
</script>

<style>
.tasklist {
  width: 500px;
  height: 50px;
  background-color: white;
  color: rgb(104, 98, 98);
  margin-left: auto;
  margin-right: auto;
  list-style: none;
}

.input-todo {
  height: 50px;
}

.input-button {
  height: 50px;
}

.delete {
  cursor: pointer;
  float: right;
}
</style>