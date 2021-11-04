<template>
  <div class="new-task">
    <input v-model="name" @keydown.enter="add" type="text" class="form-element" placeholder="Nova Tarefa?">
      
    <button @click="add" class="form-element" >+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: ''
    }
  },
  methods: {
    add() {
        this.$emit('taskAdded',{name:this.name})
        this.name = ''
    }
  }
}
</script>

<style>
  .new-task {
      margin:35px;
  }
  .form-element {
    outline: none;
    font-size: 2.3rem;
    border: 1px solid #fff;
    padding: 5px 8px 8px;
    color:#fff;
  }
  input.form-element{
    width: 500px;
    background: transparent;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
  }
 button.form-element {
   background-color:rgb(113, 113, 226) ;
   border-left: none;
   border-top-right-radius:8px;
   border-bottom-right-radius: 8px;
   cursor:pointer;
  }
   button.form-element:hover{
     background-color: rgb(36, 190, 211);
   }
</style>