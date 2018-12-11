<!--  -->
<template>
  <div class="real-contain">
    <input type="text" class="todo" placeholder="接下来要做什么？" autofocus="autofocus" @keyup.enter="addTodo">
    <Item
    :todo="item"
    v-for="item in todos"
    :key="item.id"
    @del="deleteTodo"/>
    <Tabs
    :filter1="filter1"
    :todos="todos"
    @toggle="toggleFilter"
    @clearAllCompeted="clearAllCompeted"/>
  </div>
</template>

<script>
import Item from './item'
import Tabs from './tabs'
let id = 0
export default {
  data () {
    return {
      todos: [],
      filter1: 'all'
    };
  },

  components: {
    Item,
    Tabs
  },

  computed: {
    filterTodo () {
      if (this.filter1 === 'all') {
        return this.todos
      }
      const competed = this.filter1 === 'competed'
      return this.todos.filter(todo => competed === todo.competed)
    }
  },

  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value.trim(),
        competed: false
      })
      e.target.value = ''
    },
    deleteTodo(id) {
      this.todos.splice(this.todos.findIndex(todo => todo.id === id),1)
    },
    toggleFilter(state) {
      this.filter1 = state
    },
    clearAllCompeted() {
      this.todos = this.todos.filter(todo => !todo.competed)
    }
  }
}

</script>
<style lang='less' scoped>
</style>
