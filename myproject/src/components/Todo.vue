<template>
  <div class="panel panel-primary todo">
    <div v-if="data.mode">
      <div class="panel-heading">{{ data.title }}</div>
      <div class="panel-body">
        <ul class="todo-list">
          <li v-for-key="(l, index) in data.list" class="todo-list-item">
            <table>
              <tr>
                <td style="width: 20px">
                  <input
                    type="checkbox"
                    v-model="data.list[index].status"
                    :id="l.id"
                    class="pull-left"
                  />
                </td>
                <td>
                  <label :for="l.id" class="pull-left">{{ l.value }}</label>
                </td>
              </tr>
            </table>
          </li>
          <li>
            <input class="todo-input" v-model="newVal" @keyup.enter="addTodo" />
          </li>
        </ul>
      </div>
    </div>

    <div v-else>
      <div class="panel-heading">
        <input type="text" v-model="data.title" />
      </div>
      <div class="panel-body">
        <ul class="todo-list">
          <li v-for-key="(l, index) in data.list">
            <input
              type="text"
              class="todo-input"
              v-model="data.list[index].value"
            />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo',
  props: ['data', 'index'],
  data () {
    return {
      newVal: ''
    }
  },
  methods: {
    addTodo: function () {
      if (this.newVal !== '') {
        this.data.list.push({
          value: this.newVal,
          status: false,
          id: Date.now()
        })
      }
      this.newVal = ''
    }
  }
}
</script>
<style scoped>
label {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.todo {
  float: left;
  text-align: left;
  margin: 10px;
}

.todo-list {
  padding-left: 5px;
}

.todo-list li {
  list-style: none;
  padding: 5px;
  border-radius: 5px;
}

.todo-list-item:hover {
  background-color: lightcyan;
}

.todo-list-item:hover .remove {
  background-color: whitesmoke;
  display: block;
}

.todo-list-item table {
  width: 100%;
}

.todo-input {
  border-style: none;
  border-bottom-style: dashed;
  border-bottom-width: 1px;
  outline: none;
  width: 100%;
  padding: 5px;
  margin-top: 10px;
}

input[type="checkbox"] {
  vertical-align: middle;
  height: 20px;
  width: 20px;
  margin-right: 10px;
}

.remove {
  cursor: pointer;
  display: none;
}
.remove:hover {
  color: maroon;
}
</style>
