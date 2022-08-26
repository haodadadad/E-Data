<template>
  <el-container style="min-height: 100vh;">
    <el-aside width="sideWidth+'px'" style="background-color: rgb(238, 241, 246);height:100%">
      <Aside :isCollapse="isCollapse" :logoTextShow="logoTextShow"/>
    </el-aside>

    <el-container>
      <el-header style="border-bottom: 1px solid #cccccc;">

        <Header :collapseBtnClass="collapseBtnClass" :collapse="isCollapse"/>
      </el-header>

      <el-main>
        <!--//表示当前页面的子路由围在 router——view里面展示-->
        <router-view/>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
import Aside from "@/components/Aside";
import Header from "@/components/Header";

export default {
  name: 'HomeView',
  data() {
    return {

      msg: "测试文本",
      collapseBtnClass: 'el-icon-s-fold',
      isCollapse: false,
      sideWith: 200,
      logoTextShow: true,

    }
  },

  components: {
    Aside,
    Header
  },
  methods: {
    collapse() {  //点击收缩按钮触发
      this.isCollapse = !this.isCollapse
      if (this.isCollapse) {//收缩
        this.sideWith = 64
        this.collapseBtnClass = 'el-icon-s-unfold'
        this.logoTextShow = false
      } else {//展开
        this.sideWith = 200
        this.collapseBtnClass = 'el-icon-s-fold'
        this.logoTextShow = true
      }
    },


  }
}
</script>
