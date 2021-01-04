<template>
  <div class="tab-control">
    <div :key="index" v-for="(item, index) in titles" 
          class="tab-control-item"
          :class="{active: index === currentIndex}"
          @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TabControl",
    props: {
      titles: {
        type: Array,
        default() {
          return []
        }
      }
    },
    data() {
      return {
        currentIndex: 0
      }
    },
    methods: {
      itemClick(index) {
        this.currentIndex = index;
      }
    }
  }
</script>

<style>
  .tab-control {
    display: flex;
    text-align: center;
    background-color: #fff;
  }
  .tab-control-item {
    flex: 1;
    height: 40xp;
    line-height: 40px;
  }
  .active span {
    padding: 5px;
    border-bottom: 3px solid var(--color-tint);
    color: var(--color-tint);
  }
</style>