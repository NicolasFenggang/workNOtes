<template>
  <div>
    <!-- remain显示的元素个数 size每个元素的高度 -->
  <List :items="arr" :remain='20' :size='20'>
    <template v-slot:default='{ item }'>
      <p style="margin: 0; padding: 0; height: 20px;">{{ item }}</p>
    </template>
  </List>
  </div>
</template>

<script>
import List from '../List.vue'

export default {
  name: "ListView",
  data() {
    // 动态初始化长列表数据
    let arr =[];
    for (let i = 0; i < 10000; i++) {
      arr.push(i +1)
    }
    return {
      arr,
    }
  },
  mounted(){
     console.log('arr is', this.arr);
  },
  components: {
    List
  }
}
</script>
