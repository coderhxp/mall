<template>
  <div id="tab-bar">
    <!-- 不是具名插槽, 里面可以插入多个元素 -->
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'TabBar',
    components: {

    }
  }
</script>

<style>
  #tab-bar {
    display: flex;

    position: fixed; 
    left: 0;
    right: 0;
    bottom: 0;

    box-shadow: 0 -1px 1px rgba(100, 100, 100, 0.2);
  }
</style>