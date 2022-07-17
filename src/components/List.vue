<template>
  <!-- 用户看到的容器大小 -->
  <div class="viewport" ref='viewport' @scroll="onscroll">
    <div class="scroller" ref='scroller'></div>
    <!-- list 列表需要绝对定位 -->
    <div class="list" :style="{transform: `translate(0, ${offset}px)`}">
      <div v-for="(item, index) in showItems" :key="index">
        <slot :item='item'></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: ['items', 'remain', 'size'],
  data() {
    return {
      start: 0,
      end: 20,
      offset: 0,
    }
  },
  computed: {
    showItems() {
      return this.items.slice(this.start, this.end)
    }
  },
  mounted() {
    this.initScorll()
  },
  methods: {
    initScorll() {
      // 视口和滚动条的高度
      this.$refs.viewport.style.height = this.remain * this.size + 'px'
      // 滚动条的高度是所有元素的总高
      this.$refs.scroller.style.height = this.items.length * this.size + 'px'
    },
    onscroll() {
      let count = this.$refs.viewport.scrollTop / this.size
      // 处理滚动时的小数问题
      this.start = Math.floor(count)
      this.end = this.start + this.remain
      // 视口中的元素向上滚动几个就需要下面的元素向视口中平移几个
      this.offset = this.start * this.size
    }
  }
}
</script>

<style>
.viewport {
  position: relative;
  overflow-y: scroll;
}
.list {
  position: absolute;
  left:0;
  top:0;
}
.scroller {
  background-color: aqua;
}
</style>