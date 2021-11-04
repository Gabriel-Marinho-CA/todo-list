<template>
  <div
  @click="$emit('taskStateChanged',task)"
  class="task" 
  :class="stateClass"
  >
    <span class="close" @click.stop="$emit('taskDeleted',task)">X</span>
    <p>{{task.name}}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: {type: Object, required: true}
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      }
    }
  }
}
</script>

<style>
  .task {
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2.4rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .pending {
    border-left: 12px solid rgb(155, 83, 83);
    background-color:rgb(155, 83, 83);
  }

  .done {
    color: #ddd;
    border-left: 12px solid rgb(71, 131, 79);
    background-color:rgb(71, 131, 79);
    text-decoration: line-through;
  }
  .pending .close {
    background-color: rgb(243, 127, 127);
  }
  
  .done .close {
    background-color: rgb(89, 141, 52);
  }

  .close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    width:20px;
    height:20px;
    border-radius: 10px;
    display:flex;
    justify-content: center;
  }

</style>