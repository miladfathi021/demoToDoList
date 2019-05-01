<template>
  <div>
    <vheader :list="todoList" @task="newTask"></vheader>
    <tasks :list="todoList"></tasks>
  </div>
</template>

<script>
import Vheader from '../components/Vheader.vue';
import Tasks from '../components/Tasks.vue';

export default {
  components: {Vheader, Tasks},
  data () {
    return {
      todoList: [],
      editValue: undefined
    }
  },
  methods: {
    newTask (value) {
      this.todoList.push(value);
    }
  }
}
</script>

<style scoped>

</style>
