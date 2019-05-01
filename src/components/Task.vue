<template>
  <li :class="{'is-completed': !pending}">
    <p id="title" :class="{'completedText': !pending}">{{ name }}</p>
    <div class="panel">
      <i class="fas fa-trash-alt" @click="removeItem"></i>
      <i class="fas fa-edit" v-if="pending"></i>
      <button class="button is-danger" type="button" @click="pendingFn" v-if="pending">Pending</button>
      <button class="button is-primary completed" type="button" v-if="!pending">Completed</button>
    </div>
  </li>
</template>

<script>
export default {
  props: ['name', 'tasks'],
  data () {
    return {
      titles: this.tasks,
      title: this.name,
      pending: true
    }
  },
  methods: {
    removeItem () {
      let index = this.tasks.findIndex((element) => element == this.name);
      this.tasks.splice(index, 1);
    },
    pendingFn () {
      this.pending = false;
    }
  }
}
</script>

<style scoped>
li {
  width: 100%;
  min-height: 100px;
  background-color: #ffffff;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 10px;
}
li.is-completed {
  background-color: #fdfdfd;
}
li p.completedText {
  text-decoration:line-through
}
p#title {
  display: inline-block;
  width: 77%;
  vertical-align: middle;
}
.panel {
  width: 23%;
  display: inline-block;
  vertical-align: middle;
}
.fa-trash-alt {
  margin-left: 30px;
  margin-right: 10px;
}
i.fas {
  cursor: pointer;
}
.button {
  margin-top: 5px;
  font-weight: 600;
}
.completed {
  opacity: .7;
  cursor: not-allowed;
}
</style>

