<template>
  <div class="form">
    <input type="text" class="middle" v-model="title">
    <button class="button is-white middle" type="button" @click="validation">Create</button>
  </div>
</template>

<script>

export default {
  props: ['tasks'],
  data () {
    return {
      list: this.tasks,
      title: ''
    }
  },
  methods: {
    validation () {
      if (this.title === '') {
        this.$emit('error', 'task field is required.');
        return;
      }
      if (this.title.length <= 3) {
        this.$emit('error', 'Enter at least 3 characters.');
        return;
      }
      if (this.title.length > 120) {
        this.$emit('error', 'Enter a maximum of 120 characters.');
        return;
      }
      if (this.list.find((element) => element === this.title)) {
        this.$emit('error', 'This value is duplicate.');
        return;
      }
      this.$emit('content', this.title);
      this.title = '';
      return;
    }
  }
}
</script>

<style scoped>
.form {
  height: 50px;
  margin-top: .3rem;
  border-top-left-radius: .35rem;
  border-top-right-radius: .35rem;
  line-height: 50px;
}
.form input {
  width: 80%;
  margin-left: .65rem;
  padding: 10px;
  font-size: 15px;
  border: none;
  outline: none;
  border-radius: .25rem;
}
.middle {
  vertical-align: middle;
}
.button {
  height: 2.35rem;
  margin-left: .25rem;
}

</style>

