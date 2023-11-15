<template>
  <div class="item">
    <header>
      <h1>Pinia Tasks</h1>
    </header>

    <!-- filter nav -->
    <nav class="filter">
      <button @click="filter = 'all'">All Tasks</button>
      <button @click="filter = 'favs'">Favorite Tasks</button>
    </nav>
    

    <div class="task-list" v-if="filter === 'all'">
      <p>You have {{ taskStore.totalCount  }} tasks left to do</p>
      <div v-for="task in taskStore.tasks" key="tasks.id">
        <TaskDetails :task="task" />
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>You have {{ taskStore.favsCount  }} favorite tasks left to do</p>

      <div v-for="task in taskStore.favs">
        <TaskDetails :task="task" />
      </div>
    </div>
  </div>
</template>

<script>
import { useTaskStore } from "../store/TaskStore";
import TaskDetails from "./TaskDetails.vue";
import { ref } from "vue";

export default {
  components: { TaskDetails },
  setup() {
    const taskStore = useTaskStore();
    const filter = ref("all");

    return { taskStore, filter};
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
