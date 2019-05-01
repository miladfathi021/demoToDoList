<template>
  <div>
    <article class="message is-danger">
      <div class="message-header">
        <p>{{ title }}</p>
        <button class="delete" aria-label="delete" @click="closeMessage"></button>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  props: ['title'],
  methods: {
    closeMessage () {
      this.$emit('closeMessage');
    }
  }
}
</script>

<style scoped>
.message {
  box-shadow: 0 0 10px rgba(0, 0, 0, .4);
  position: relative;
  animation: fadeIn .2s linear;
}
@keyframes fadeIn {
  from {
    top: -20px;
    opacity: 0;
  }
  to {
    top: 0;
    opacity: 1;
  }
}
</style>

