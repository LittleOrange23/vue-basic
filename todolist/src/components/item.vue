<!--  -->
<template>
  <div class="item" :class="['todo-item', todo.competed ? 'competed' : '']">
    <input type="checkbox" class="toggle" v-model="todo.competed">
    <label>{{todo.content}}</label>
    <button @click="deleteTodo"></button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    todo: {
      type: Object,
      require: true
    }
  },
  components: {},

  computed: {},

  methods: {
    deleteTodo() {
      this.$emit('del', this.todo.id)
    }
  }
};
</script>
<style lang='less' scoped>
</style>
