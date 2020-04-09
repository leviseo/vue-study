<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem">
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="removeBtn" @click="removeTodo(todoItem, index)">
          <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit("removeTodo", todoItem, index);
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  text-align: left;
}
li {
  display: flex;
  align-items: center;
  height: 50px;
  min-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  border-radius: 5px;
  background-color: #fff;
}
.checkBtn {
  margin-right: 5px;
  line-height: 45px;
  color: #62acde;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
/* transiton-group */
.list-item {
	display:inline-block;
	margin-right: 10px;
}
.list-move {
	transition: transform 1s;
}
.list-enter-active,
.list-leave-active {
	transition: all 1s;
}
.list-enter,
.list-leave-to {
	opacity: 0;
	transform: translateY(30px);
}
</style>
