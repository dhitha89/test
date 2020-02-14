<template>
 <div class="container">
    <h1> TO DO LIST</h1>
    <md-field>
      <md-input v-model="currentTodo" @keydown.enter="addTodo()" placeholder="Add a todo"></md-input>
    </md-field>
    <ul class="todos">
      <div class="row">
        <li v-for="todo in todos" :key="todo.id">
          <h3><md-icon>send</md-icon>&nbsp;&nbsp;{{ todo.label }}
            <div style="float:right">
              <md-button @click="editTodo(todo)" class="md-raised" :md-ripple="false">Edit</md-button>
              <md-button @click="removeTodo(todo)" class="md-raised md-accent">Delete</md-button>
            </div>
          </h3>
          <hr>
        </li>
      </div>
    </ul>

  </div>
</template>


<script>
export default {
  data() {
    return {
      todos: [],
      currentTodo: '',
      editTodoId:'',
    };
  },
  name: 'LayoutHorizontalGutter',
  methods: {
    addTodo() {
      this.todos.push({
        id: this.todos.length,
        label: this.currentTodo,
        completed: false
        });
    },
    removeTodo(todo) {
      var index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
  }
};
</script>

<style>
  body{
    margin:5% 10%!important;
  }

  .container{
    min-height:100px;
    background-color:gray;
    padding:2%;
  }
  .container h1{
    text-align:center;
    margin-bottom:50px;
    text-decoration:underline;
  }
  ul{
    list-style-type:none;
  }
 .md-layout-item {
    height: 40px;
  }
  .todos .md-raised{
    margin-top:-5px;
  }
</style>
