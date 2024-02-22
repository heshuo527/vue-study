<template>
  <div>
    <input type="text" @change="handleValue" />
    <button @click="addTodo">添加</button>
    <!-- 遍历todos -->
    <ul>
      <li v-for="{ id, name } in todos" :key="id">
        <button @click="handleDelete(index)">删除</button>
        <button @click="handleDelete(index)">完成</button>
        {{ name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      inputValue: "",
    };
  },
  methods: {
    /**
     * 添加一个todo
     * @param {obj}
     */
    addTodo() {
      this.todos.push({
        id: new Date().getTime(),
        name: this.inputValue,
        done: false,
      });
      console.log("11111", this.todos);
    },
    /**
     * 监听输入框的值
     * @param {*} e 事件对象
     */
    handleValue(e) {
      const { value } = e.target;
      this.inputValue = value;
    },
    handleDelete(v) {
      console.log(v);
      const { id: i } = v[0];
      const copyTodos = this.todos.filter(({ id }) => id !== i);
      this.todos = copyTodos;
    },
  },
};
</script>

<style></style>
