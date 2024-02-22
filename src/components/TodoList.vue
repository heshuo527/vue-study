<template>
  <div>
    <input type="text" @change="handleValue" />
    <button @click="addTodo">添加</button>
    <!-- 遍历todos -->
    <ul>
      <li
        v-for="{ id, name, done } in todos"
        :key="id"
        :style="{
          color: done ? 'red' : '',
          textDecoration: done ? 'line-through' : '',
        }"
      >
        <button @click="handleDelete(id)">删除</button>
        <button @click="handleDone(id)">完成</button>
        {{ name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  // 全局数据
  data() {
    return {
      todos: [],
      inputValue: "",
    };
  },
  methods: {
    /**
     * 添加一个todo
     * @param {*} obj
     */
    addTodo() {
      this.todos.push({
        id: new Date().getTime(),
        name: this.inputValue,
        done: false,
      });
    },
    /**
     * 监听输入框的值
     * @param {*} e 事件对象
     */
    handleValue(e) {
      const { value } = e.target;
      this.inputValue = value;
    },
    /**
     * 删除一个todo
     * @param {*} id
     */
    handleDelete(id) {
      const copyTodos = this.todos.filter((p) => p.id !== id);
      this.todos = copyTodos;
    },
    /**
     * 完成一个todo
     * @param {*} id
     */
    handleDone(id) {
      const data = [...this.todos];
      data.forEach((item) => {
        if (item.id === id) {
          item.done = !item.done;
        }
      });
      this.todos = data;
    },
  },
};
</script>

<style></style>
