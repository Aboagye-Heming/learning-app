<template>
  <div class="item">
    <header>
      <h1>Pinia Tasks</h1>
    </header>
    <div class="task-list">
      <div v-for="task in taskStore.tasks" key="tasks.id">
        <TaskDetails :task="task" />
      </div>
    </div>
  </div>
</template>

<script>
import { useTaskStore } from "../store/TaskStore";
import TaskDetails from "./TaskDetails.vue";

export default {
  components:{TaskDetails},
  setup() {
    const taskStore = useTaskStore();

    return { taskStore };
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
