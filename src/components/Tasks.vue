<template>
  <div class="tasks">
    <ul>
      <task class="task" v-for="title in titles" :key="title" :name="title" :tasks="titles"></task>
    </ul>
  </div>
</template>

<script>
import Task from '../components/Task.vue';
export default {
  components: {Task},
  props: ['list'],
  data () {
    return {
      titles: this.list
    }
  }
}
</script>

<style>
.tasks {
  width: 100%;
  height: calc(100vh - 200px);
  background-color: #EFEFEF;
  padding: 10px;
  overflow: scroll;
}

</style>
