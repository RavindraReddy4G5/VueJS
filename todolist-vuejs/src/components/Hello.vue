<template>
  <div class="c1">
    <nav class="navbar navbar-inverse">
      <div class="container-fluid">
        <div class="navbar-header">
          <button class="pull-left btn btn-info" v-on:click="addTodo">
            <span class="glyphicon glyphicon-plus"></span>
            New List
          </button>
        </div>
      </div>
    </nav>

    <div class="container">
      <div v-for="(todo, i) in todos">
        <todo :index="i" :data="todos[i]"></todo>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo.vue";

export default {
  components: { Todo },
  name: "hello",
  data() {
    return {
      todos: [
        {
          id: Date.now(),
          mode: true,
          list: [{ value: "", status: false, id: 234 }],
        },
      ],
    };
  },

  methods: {
    addTodo() {
      this.todos.push({
        id: Date.now(),
        mode: true,
        list: [],
      });
    },
  },
};
</script>
<style scoped>
.navbar {
  border-radius: 0px !important;
  background: blue;
}
.c1 {
  background: blue;
}
</style>
