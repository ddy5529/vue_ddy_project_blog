<template>
  <el-tabs aria-label="书签页" v-model="activeName" @tab-click="handleClick" :tab-position="tabPosition">
    <el-tab-pane label="常用网站" name="first">
      <el-row>
        <el-col :span="8" aria-label="论坛">
          <div class="grid-content bg-purple">
            <h2>论坛</h2>
            <ol>
              <li><a href="http://www.html5tricks.com/" style="color: blue" target="_blank">HTML5 Tricks 网页特效素材网站</a></li>
              <li><a href="https://www.csdn.net/" style="color: blue" target="_blank">CSDN 国内程序员论坛网站</a></li>
              <li><a href="https://juejin.im/welcome/frontend" style="color: blue" target="_blank">掘金——开发者成长之路</a></li>
            </ol>
          </div>
        </el-col>
        <el-col :span="8" aria-label="学习网址"><div class="grid-content bg-purple-light">
          <h2>学习网址</h2>
          <ol>
            <li><a href="https://www.imooc.com/" style="color: blue" target="_blank">慕课网 免费学习编程的视频网站</a></li>
            <li><a href="http://www.runoob.com/nodejs/nodejs-mysql.html" style="color: blue" target="_blank">菜鸟教程-node</a></li>
            <li><a href="https://dafrok.github.io/vue-baidu-map/#/zh/map/bm-view" style="color: blue" target="_blank">基于VUE的百度地图文档</a> </li>
            <li><a href="https://cn.vuejs.org/v2/guide/" target="_blank" style="color: blue">VUE的官方文档</a></li>
          </ol>
        </div></el-col>
        <el-col :span="8" aria-label="私人链接"><div class="grid-content bg-purple">
          <h2>私人链接</h2>
          <ol>
            <li><a href="https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=sandbox/login" style="color: blue" target="_blank">微信公众号后台管理器</a></li>
            <li><a href="https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1445241432" style="color: blue" target="_blank">微信开发者文档</a></li>
            <li><a href="http://xkddy.xyz/" style="color: blue" target="_blank">我的域名</a></li>
            <li><a href="https://www.aliyun.com/" style="color: blue" target="_blank">阿里云服务后台</a></li>
            <li><a href="https://github.com/PanJiaChen/vueAdmin-template/blob/master/README-zh.md" style="color: blue" target="_blank">此项目的模板——VUE后台管理</a></li>
          </ol>
        </div></el-col>
      </el-row>
    </el-tab-pane>
    <el-tab-pane label="工具网址" name="second">
      <el-row>
        <el-col :span="8">
          <div class="grid-content bg-purple">
            <ol>
              <li><a href="https://c.runoob.com/" target="_blank" style="color: blue">菜鸟教程工具箱</a></li>
            </ol>
          </div>
        </el-col>
        <el-col :span="8"><div class="grid-content bg-purple-light">
          <ol>
            <li><a href="#" target="_blank" style="color: blue">2</a></li>
          </ol>
        </div></el-col>
        <el-col :span="8"><div class="grid-content bg-purple">
          <ol>
            <li><a href="#" target="_blank" style="color: blue">3</a></li>
          </ol>
        </div></el-col>
      </el-row>
    </el-tab-pane>
    <el-tab-pane label="重要网址" name="third">
      <ol>
        <li><a href="https://panjiachen.github.io/vue-element-admin-site/#/zh-cn/chart" style="color: red">做个这个模板的WIKI文档</a></li>
        <li><a href="https://segmentfault.com/a/1190000009275424" style="color: blue">手摸手，带你用vue撸后台 系列一(基础篇)</a> </li>
      </ol>
    </el-tab-pane>
  </el-tabs>
</template>
<style>
  div ol li {
    margin-top: 20px;
  }
  .el-col {
    border-radius: 4px;
  }

  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    padding-left: 8px;
    padding-top: 5px;
    padding-bottom: 5px;
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>
<script>
  export default {
    data() {
      return {
        activeName: 'first',
        tabPosition: 'left'
      }
    },
    methods: {
      handleClick(tab, event) {
        console.log(tab, event, '小工具的切换')
      }
    }
  }
</script>
