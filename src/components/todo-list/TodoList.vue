<template>
  <ul class="list-group">
    <li class="list-group-item d-flex justify-content-between align-items-center" 
    v-for="item in list" 
    :key="item.key">
      <!-- 复选框 -->
      <div class="checkbox">
        <label> <input type="checkbox" /> 
        </label>
      </div>
      <!-- 徽章 -->
       <span class="badge badge-success ">完成</span>
       <span class="badge">未完成</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    list: {
      type: Array,
      require: true,
      default: [],
    },
  },
};
</script>

<style lang="less" scoped>
.list-group {
  width: 400px;
}
</style>

