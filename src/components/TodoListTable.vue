<template>
  <div>
    <h3>{{ moment().format("YYYY年MM月DD日") }} 任务清单</h3>
    <div style="margin-top: 15px">
      <el-input
        placeholder="请输入任务"
        v-model="inputValue"
        @change="changeValue($event)"
        @keydown="handleAddTask($event)"
      >
        <template slot="append">
          <el-button type="primary" size="mini" @click="handleAddTask($event)"
            >添加任务</el-button
          >
        </template>
      </el-input>
    </div>
    <el-table :data="todos" style="width: 100%">
      <el-table-column prop="task" label="序号" width="180">
        <template slot-scope="{ $index }">
          {{ $index + 1 }}
        </template>
      </el-table-column>
      <el-table-column prop="task" label="任务" width="180">
        <template slot-scope="{ row }">
          <span :class="[row.done ? 'done' : '']">{{ row.task }}</span>
        </template>
      </el-table-column>
      <el-table-column prop="time" label="时间" width="180">
        <template slot-scope="{ row }">
          {{ moment(row.time).format("YYYY-MM-DD HH:mm:ss") }}
        </template>
      </el-table-column>
      <el-table-column label="操作" width="280">
        <template slot-scope="{ row, $index }">
          <el-button
            type="primary"
            size="mini"
            @click="handleDone(row, $index)"
            >{{ row.done ? "取消" : "完成" }}</el-button
          >
          <el-button type="primary" size="mini" @click="handelEdit(row, $index)"
            >编辑</el-button
          >
          <el-button type="danger" size="mini" @click="handleRemove($index)"
            >删除</el-button
          >
        </template>
      </el-table-column>
    </el-table>
    <TodoListForm :modal="modal" />
  </div>
</template>

<script>
import moment from "moment";
import TodoListForm from "./TodoListForm.vue";
export default {
  components: {
    TodoListForm,
  },
  data() {
    return {
      todos: [
        {
          task: "抱着老婆睡觉!",
          done: true,
          time: new Date().getTime(),
        },
      ],
      inputValue: "",
      modal: {
        visible: false,
        data: {},
      },
    };
  },
  methods: {
    // 监听输入框的值
    changeValue(e) {
      this.inputValue = e;
    },
    // 完成
    handleDone(r, i) {
      const { done } = r;
      this.todos[i].done = !done;
    },
    // 添加一个任务
    handleAddTask(e) {
      console.log(e);
      const todo = {
        task: this.inputValue,
        done: false,
        time: new Date().getTime(),
      };
      this.todos.push(todo);
      this.inputValue = "";
    },
    // 删除一个
    handleRemove(i) {
      const data = this.todos;
      data.splice(i, 1);
      this.todos = data;
    },
    // 编辑
    handelEdit(r, i) {
      this.modal = {
        visible: true,
        data: r,
      };
    },
  },
  // 引入的依赖需要在此引用到页面
  computed: {
    moment() {
      return moment;
    },
  },
};
</script>

<style>
.done {
  color: red;
  text-decoration: line-through;
}
</style>
