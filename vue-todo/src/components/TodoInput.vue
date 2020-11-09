<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <!--<button v-on:click="addTodo">add</button>-->
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa fa-plus addBtn"></i>
    </span>
    <Modal v-if="showModal" @close="showModal = false">
      <!--
        you can use custom content here to overwrite
        default content
      -->
      <h3 slot="header">
        경고!
      <i class="fa fa-times closeModalBtn" v-on:click="showModal=false"></i>
      </h3>
      <p slot="body">할 일을 입력해주세요~!</p>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  data(){
    return{
      newTodoItem:'',
      showModal: false
    }
  },
  methods:{
    addTodo(){
      //console.log(this.newTodoItem);
      // 저장하는 로직
      //localStorage.setItem('key', 'value');
      if(this.newTodoItem !== ''){
        //this.$emit('addTodoItem', this.newTodoItem);
        this.$store.commit('addOneItem', this.newTodoItem);
        this.clearInput();
      }else{
        this.showModal = !this.showModal;
      }
    },
    clearInput(){
      this.newTodoItem='';
    }
  },
  components:{
    Modal
  }
}
</script>

<style scoped>
  input:focus{
    outline:none
  }
  .inputBox{
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius:5px;
  }
  .inputBox input{
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer{
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width:3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBtn{
    color:white;
    vertical-align: middle;
  }
  .closeModalBtn{
    color:#42b983;
  }
</style>