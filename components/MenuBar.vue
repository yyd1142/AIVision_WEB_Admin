<template>
  <div class="main-wrap">
    <div class="menu-wrap">
      <div class="title-top">{{languageDatas.MenuList[language]}}</div>
      <el-menu :default-active="defaultActive" :default-openeds="defaultOpeneds" :unique-opened="true" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose">
        <el-submenu index="1">
          <template slot="title">
            <div class="menu-cell">
              <i class="iconfont icon-yibiaopan icon"></i>
              <span class="title">{{languageDatas.BackstageManagement[language]}}</span>
            </div>
          </template>
          <el-menu-item-group>
            <el-menu-item index="1-1" @click="_onPress('Configuration')">{{languageDatas.StoreSetting[language]}}</el-menu-item>
            <el-menu-item index="1-2" @click="_onPress('Configuration/System')">{{languageDatas.SystemConfiguration[language]}}</el-menu-item>
          </el-menu-item-group>
        </el-submenu>
      </el-menu>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
      }
    },
    props:{
      language: String,
      defaultActive: String,
      defaultOpeneds: Array
    },
    computed: {
      languageDatas() {
        return this.$store.getters.languageDatas;
      },
    },
    methods: {
      handleOpen(key, keyPath) {
        // console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        // console.log(key, keyPath);
      },
      _onPress(path) {
        path = `/${path}?language=${this.language}`;
        window.location.href = path;
      }
    }
  }
</script>

<style lang="less">
  @import url("../static/style/config.less");

  .main-wrap {
    .el-menu > .el-submenu {
      padding: 10px 0;
    }
    .menu-wrap {
      width: 100%;
      min-height: 100vh;
      -moz-box-shadow: 2px 0px 8px #f2f2f2; /* 老的 Firefox */
      box-shadow: 2px 0px 8px #f2f2f2;
      .title-top {
        width: 100%;
        background: @mainColor;
        height: 80px;
        line-height: 80px;
        color: #fff;
        font-size: 20px;
        padding-left: 20px;
        -moz-box-shadow: 0px 2px 8px #f2f2f2; /* 老的 Firefox */
        box-shadow: 0px 2px 8px #f2f2f2;
        box-sizing: border-box;
      }
    }
    .menu-cell {
      width: 100%;
      .icon {
        color: @mainColor;
        font-size: 24px;
      }
      .icon-small {
        color: @mainColor;
        font-size: 24px;
      }
      .title {
        font-size: 16px;
        padding-left: 15px;
      }
    }
  }
</style>

