<template>
  <el-dialog title="编辑活动" :visible.sync="modal.visible">
    <el-form :model="form">
      <el-form-item label="名称" :label-width="formLabelWidth">
        <el-input v-model="form.task" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="完成" :label-width="formLabelWidth">
        <el-switch v-model="form.done" autocomplete="off"></el-switch>
      </el-form-item>
    </el-form>
    <div slot="footer" class="dialog-footer">
      <el-button @click="modal.visible = false"> 取 消</el-button>
      <el-button type="primary" @click="onSubmit">确 定</el-button>
    </div>
  </el-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialogFormVisible: false,
      form: {
        task: "",
        done: "",
      },
      formLabelWidth: "120px",
      dialogVisible: true,
    };
  },
  props: ["modal"],
  updated() {
    this.form = this.modal.data || {};
  },
  methods: {
    onSubmit() {
      console.log("提交", this.form, this.modal.data);
      this.modal.visible = false;
    },
  },
};
</script>

<style></style>
