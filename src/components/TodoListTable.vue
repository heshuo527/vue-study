<template>
  <div>
    <div style="margin-top: 15px">
      <el-input
        placeholder="请输入任务"
        v-model="input2"
        @change="changeValue($event)"
      >
        <template slot="append">
          <el-button type="primary" size="mini" @click="handleAddTask"
            >添加任务</el-button
          >
        </template>
      </el-input>
    </div>
    <el-table :data="todos" style="width: 100%">
      <el-table-column prop="task" label="序号" width="180">
        <template slot-scope="{ row, $index }">
          {{ $index + 1 }}
        </template>
      </el-table-column>
      <el-table-column prop="task" label="任务" width="180"> </el-table-column>
      <el-table-column prop="time" label="时间" width="180">
        <template slot-scope="{ row }">
          {{ moment(row.time).format("YYYY-MM-DD HH:mm:ss") }}
        </template>
      </el-table-column>
      <el-table-column label="操作" width="280">
        <template slot-scope="{ row }">
          <el-button type="primary" size="mini" @click="handleDone(row)"
            >完成</el-button
          >
          <el-button type="primary" size="mini">编辑</el-button>
          <el-button type="danger" size="mini">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import moment from "moment";
export default {
  data() {
    return {
      todos: [
        {
          task: "抱着老婆睡觉!",
          done: true,
          time: new Date().getTime(),
        },
      ],
    };
  },
  methods: {
    changeValue(e) {
      console.log(11111, e);
      const { value } = e.target;
    },
    handleDone(r) {
      console.log(11111, r);
    },
    handleAddTask() {
      console.log(2222);
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

<style></style>
