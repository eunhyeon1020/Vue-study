<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo"> 
    <!-- <button v-on:click="addTodo">add</button> -->
    <span class="addContainer" v-on:click="addTodo"> 
      <i class="fas fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      newTodoItem : ""
    }
  },

  methods : {
    addTodo : function() {
      if(this.newTodoItem !== ''){
        //로컬 스토리지에 저장
        var obj = {completed : false, item: this.newTodoItem};
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearInput();
      }
    }, 
    clearInput : function () {
      //input 박스 초기화화
      this.newTodoItem = '';
    }
  }
}

</script>

<style scoped>
  input:focus {
    outline : none;
  }

  .inputBox {
    display: inline-block;
    background: white;
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }

  .inputBox input {
    border-style: none;
    font-size: 0.9rem;
  }

  .addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763fb);
    display : block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
  }

  .addBtn {
    color: white;
    vertical-align: middle;
  }
</style>