<template>
  <div class="tasks-grid">
    <template v-if="tasks.length " > 
        <Task 
          v-for="(task,i) in tasks" 
          :key="task.name" 
          @taskDeleted ="$emit('taskDeleted',i)"
          @taskStateChanged ="$emit('taskStateChanged',i)"
          :task="task"
        > {{task.name}} </Task>  

    
    </template> 
    <p v-else class="no-task">Sua vida esta em dia :)</p>
  </div>
</template>

<script>
import Task from './Task.vue'
export default {
  components: {Task},
  props: {
    tasks: {type: Array, required: true}
  }
}
</script>

<style>
  .tasks-grid {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }
  .tasks-grid .task {
    margin: 10px;
  }
  .no-task {
    font-size: 3rem;
    font-weight: 300;
  }
</style>