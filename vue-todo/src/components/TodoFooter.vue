<template>
  <div class="clearAllContainer shadow">
    <span class="clearAllBtn" v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods:{
    clearTodo:function (){
      localStorage.clear();
    }
  }
}
</script>

<style scoped>
.clearAllContainer{
  width:8.5rem;
  height:50px;
  line-height:50px;
  background:#fff;
  border-radius:5px;
  margin: 0 auto;
}
.clearAllBtn{
  color:red;
  display:block;
  cursor: pointer;
}
</style>