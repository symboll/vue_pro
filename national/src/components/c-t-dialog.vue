<template>
  <div>
    <el-dialog
      :title="title"
      :visible="visible"
      :close-on-click-modal="false"
      :close-on-press-escape="false"
      @close="handleCancel"
      :width="width"
    >
      <slot></slot>
      <span slot="footer" class="dialog-footer">
        <el-button v-if="showConfirm" type="primary" @click="handleConfirm">{{ confirmButtonText }}</el-button>
        <el-button @click="handleCancel">{{ showConfirm ? '取 消': '关 闭' }} </el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data () {
    return {}
  },
  props: {
    confirmButtonText: {
      type: String,
      default: "确 定"
    },
    title: {
      type:String,
      required: true
    },
    visible: {
      type:Boolean,
      default: false
    },
    width: {
      type: String,
      default: "460px"
    },
    showConfirm: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    handleConfirm () {
      this.$emit('confirm')
    },
    handleCancel () {
      this.$emit('close')
    }
  }
}

</script>
<style lang="scss" scoped>
::v-deep .el-dialog__header {
  border-bottom: 1px solid #F2F2F2;
}
::v-deep .el-dialog__footer {
  border-top: 1px solid #F2F2F2;
}
::v-deep .el-dialog__body {
  padding: 20px;
}
::v-deep .el-icon-close:before {
  color: #787878;
  font-weight: bold;
  font-size: 20px;
}
</style>