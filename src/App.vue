<template>
  <div>
    <div id="app">
      <HelloWorld
        url="https://tse3-mm.cn.bing.net/th/id/OIP-C.DR0pzvBSWjhtHKlP7NmcEgHaE8?w=256&h=180&c=7&r=0&o=5&dpr=2&pid=1.7"
        :size="100"
      />
      <TodoList />
      <TodoListTable />
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/Avatar.vue";
import TodoList from "./components/TodoList.vue";
import TodoListTable from "./components/TodoListTable.vue";

export default {
  components: {
    HelloWorld,
    TodoList,
    TodoListTable,
  },
};
</script>

<style>
#app {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
