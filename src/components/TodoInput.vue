<template>
  <div>
    <input type="text" v-model="newTodoItem">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus-square"></i>
    </span>

    <modal v-if="showModal" @close="showModel = false">
      <h3 slot="header">경고</h3>
      <span slot="footer" @click="showModal = false">
        할 일을 입력하세요 <i class="closeModalBtn fa fa-times"></i>
      </span>
    </modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  data(){
    return {
      newTodoItem: '',
      showModal: false
    }
  },
  props: ['propsdata'],
  methods: {
    addTodo(){
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
				this.$emit('addTodo', value)
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      } 
    },
    clearInput(){
      this.newTodoItem = "";
    }
  },
  components: {
    Modal: Modal
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