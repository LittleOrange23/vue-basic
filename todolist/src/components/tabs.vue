<!--  -->
<template>
  <div class="tabs">
    <span>{{unFinishedTodoLength}} items left</span>
    <span v-for="state in states" :key="state" :class="[state, filter1===state ? 'active' : '']" @click="toggleFilter(state)">
      <span>{{state}}</span>
    </span>
    <span @click="clearAllCompeted">clear Competed</span>
  </div>
</template>

<script>
export default {
  data () {
    return {
      states: ['all', 'active', 'competed']
    };
  },
  props: {
    filter1: {
      type: String,
      required: true
    },
    todos:{
      type: Array,
      required: true
    }
  },
  components: {},

  computed: {
    unFinishedTodoLength() {
      return this.todos.filter(todo => !todo.competed).length
    }
  },

  methods: {
    toggleFilter(state){
      this.$emit('toggle', state)
    },
    clearAllCompeted() {
      this.$emit('clearAllCompeted')
    }
  }
}

</script>
<style lang='less' scoped>
</style>
