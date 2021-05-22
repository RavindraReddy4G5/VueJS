<template>

  <div class="panel panel-primary todo">
    <div v-if="data.mode">
      <div class="panel-heading">{{data.title}}</div>
      <div class="panel-body">
        <ul class="todo-list">
          <li v-for="(l, index) in data.list" class="todo-list-item">
            <table>
              <tr>
                <td><label :for="l.id"  class="pull-left">{{l.value}}</label></td>
              </tr>
            </table>
          </li>
          <li><input class="todo-input" v-model="newVal" placeholder="+Add New List" @keyup.enter="addTodo"/></li>
        </ul>
      </div>
    </div>

    <div v-else>
      <div class="panel-heading">
        <input type="text" v-model="data.title"/>
      </div>
      <div class="panel-body">
          <ul class="todo-list">
            <li v-for="(l, index) in data.list">
              <input type="text" class="todo-input"  v-model="data.list[index].value"/>
            </li>
          </ul>
         
      </div>
    </div>

  </div>


</template>

<script>
  export default {
    name: 'todo',
    props:["data", "index"],
    data() {
      return {
        newVal: ''
      }
    },
    methods: {
      addTodo: function(){
        if(this.newVal !== "") this.data.list.push({value: this.newVal, status: false, id: Date.now()});
        this.newVal = '';
      },
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  label{
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .todo{
    float: left;
    text-align: left;
    margin: 10px;
  }

  .todo-list{
    padding-left: 5px;
  }

  .todo-list li{
    list-style: none;
    padding: 5px;
    border-radius: 5px;
  }
  .todo-list-item table{
    width: 100%;
  }

  .todo-input{
    border-style: none;
    border-bottom-style: dashed;
    border-bottom-width: 1px;
    outline: none;
    width: 100%;
    padding: 5px;
    margin-top: 10px;
  }
</style>
