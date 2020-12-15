<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    // props中定义path是用来接收父组件传过来的path, 也就是路径, 类型是字符串类型
    path: String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
  data() {
    return {
      // isActive: true,
      // path: '/home'
    }
  },
  computed: {
    isActive() {
      // 那个路由处于活跃, 那个路由就是$route
      // /home -> item1(/home) = true
      // /home -> item1(/category) = false
      // /home -> item1(/cart) = false
      // /home -> item1(/profile) = false
      // == -1 说明this.$route.path字符串中找不到this.path字符串, 找到就不等于-1

      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      // this.isActive 判断是否处于活跃状态
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemClick() {
      if(this.path != this.$route.path) {
        this.$router.replace(this.path)
      }
      // this.$router.replace(this.path)
    }
  }
}
</script>

<style>
  .tab-bar-item {
    /* 之间距离均等分 */
    flex: 1;
    text-align: center;
    height: 49px;
    background-color: #f2f2f2;
    font-size: 14px;
  }

  .tab-bar-item img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    margin-bottom: 1px;
    /* 图片下面默认会有3px, 去掉这个3px */
    vertical-align: middle;
  }

  /* .active {
    color: red;
  } */
</style>