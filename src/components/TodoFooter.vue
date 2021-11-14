.
<template>
  <div class="clearAllContainer ">
    <span class="clearAllBtn" v-on:click="clearTodo">
      clear all
    </span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo: function() {
      localStorage.clear();
    }
  }
};
</script>

<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: #fff;
  border-radius: 5px;
  margin: auto;
}
.clearAllBtn {
  color: #e20303;
  display: block;
}
</style>
