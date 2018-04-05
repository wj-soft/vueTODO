<template>
  <div>
    <input type="text" v-model="newTodoItem">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus-square"></i>
    </span>
  </div>
</template>

<script>
export default {
  data(){
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo(){
      if(this.newTodoItem !== ""){
        var value = this.newTodoItem && this.newTodoItem.trim();
        localStorage.setItem(value, value)
        this.clearInput();
      } 
    },
    clearInput(){
      this.newTodoItem = "";
    }
  }
}
</script>

<style>
  input:focus {
    outline: none;
  }
  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inpuxBox input {
    border-style: none;
    font-size: 0.9rem;
  }
 
  .addBtn {
    color: blueviolet;
    vertical-align: middle;
  }
</style>