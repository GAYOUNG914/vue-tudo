<template>
  <div>
    <ul>
      <li
        v-for="(todoItem, index) in propsdata"
        v-bind:key="todoItem.item"
        class="shadow"
      >
        <i
          class="checkBtn fa fa-check "
          aria-hidden="true"
          v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleComplete(todoItem, index)"
        ></i>
        <span v-bind:class="{ textCompleted: todoItem.completed }">{{
          todoItem.item
        }}</span>
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
      <!-- <li>1</li>
      <li>12</li>
      <li>134</li> -->
    </ul>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo: function(todoItem, index) {
      console.log(todoItem, index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    toggleComplete: function(todoItem, index) {
      todoItem.completed = !todoItem.completed;
      //   로컬스토리지의 데이터를 갱신하는 부분
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  }
};
</script>

<style>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 46px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  line-height: 50px;
  margin-left: auto;
  color: #de4343;
}
</style>
