<template>
  <div class="header">
    <h1 class="title">ToDo List</h1>
    <vinput :tasks="titles" @error="showError" @content="task"></vinput>
    <errorMessage class="mt-1" :title="error" v-if="error.length > 3" @closeMessage="error = ''"></errorMessage>
  </div>
</template>

<script>
import Vinput from '../components/Vinput.vue';
import ErrorMessage from '../components/ErrorMessage.vue';

export default {
  components: {Vinput, ErrorMessage},
  props: ['list'],
  data () {
    return {
      titles: this.list,
      error: ''
    }
  },
  methods: {
    showError (value) {
      this.error = value;
    },
    task (value) {
      this.$emit('task', value);
    }
  }
}
</script>

<style scoped>
.header {
  background-color: #8D00FF;
  font-family: 'Roboto-bold';
  height: 200px;
}
.title {
  color: #ffffff;
  text-align: center;
  padding-top: 50px;
}
</style>
