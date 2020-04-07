<template>
  <el-dialog :visible.sync="dialogFormVisible" class="register" width="600px" :show-close="false">
      <div class="title" slot="title">用户注册</div>

  </el-dialog>
</template>

<script>
export default {
    data() {
        return {
            dialogFormVisible: false
        };
    },
}
</script>

<style lang="less">
    .register {
        .title {
            height: 53px;
            background: rgba(3,192,249,1);
            color:#fff;
            text-align: center;
            line-height: 53px;
        }
        .el-dialog_header {
            padding:0;
        }
    }
</style>