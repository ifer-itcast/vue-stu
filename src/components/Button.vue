<template>
  <!-- 禁用的时候除了样式是禁用的，按钮本身也要是禁用的 -->
  <button
    class="el-button"
    :disabled="disabled || loading"
    :autofocus="autofocus"
    :class="[
      type ? `el-button--${type}` : '',
      size ? `el-button--${size}` : '',
      {
        'is-plain': plain,
        'is-round': round,
        'is-circle': circle,
        'is-disabled': disabled,
        'is-loading': loading
      }
    ]"
    @click="$emit('click', $event)"
  >
    <i v-if="loading" class="el-icon-loading"></i>
    <!-- 只有传递了 icon 才需要展示，同时 loading 是 false 处于关闭状态，打开状态不需要展示 icon -->
    <i v-if="icon && !loading" :class="icon"></i>
    <!-- 默认插槽里面有内容才需要展示 -->
    <span v-if="$slots.default"><slot></slot></span>
  </button>
</template>

<script>
export default {
  name: 'ElButton',
  props: {
    type: {
      type: String
    },
    plain: {
      type: Boolean,
      default: false
    },
    round: {
      type: Boolean,
      default: false
    },
    circle: {
      type: Boolean,
      default: false
    },
    icon: {
      type: String
    },
    disabled: {
      type: Boolean,
      default: false
    },
    loading: {
      type: Boolean,
      default: false
    },
    size: {
      type: String
    },
    autofocus: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="less" scoped></style>
