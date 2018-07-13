<template>
  <el-row class="container">
    <!--左侧导航-->
    <el-col :span="3"  style='height: 100%'>
      <aside :class="{showSidebar:!collapsed}">
        <div class="topbar-logo topbar-btn">
          <a href="/"><img src="../assets/images/logo_zh_CN.png"></a>
        </div>
        <!--展开折叠开关-->
        <!--<div class="menu-toggle" @click.prevent="collapse">-->
        <!--<i class="iconfont icon-menufold" v-show="!collapsed"></i>-->
        <!--<i class="iconfont icon-menuunfold" v-show="collapsed"></i>-->
        <!--</div>-->
        <!--导航菜单-->
        <el-menu :default-active="defaultActiveIndex" router :collapse="collapsed" @select="handleSelect">
          <template v-for="(item,index) in $router.options.routes" v-if="item.menuShow">
            <el-submenu v-if="!item.leaf" :index="index+''">
              <template slot="title"><i :class="item.iconCls"></i><span slot="title">{{item.name}}</span></template>
              <el-menu-item v-for="term in item.children" :key="term.path" :index="term.path" v-if="term.menuShow"
                            :class="$route.path==term.path?'is-active':''">
                <i :class="term.iconCls"></i><span slot="title">{{term.name}}</span>
              </el-menu-item>
            </el-submenu>
            <el-menu-item v-else-if="item.leaf&&item.children&&item.children.length" :index="item.children[0].path"
                          :class="$route.path==item.children[0].path?'is-active':''">
              <i :class="item.iconCls"></i><span slot="title">{{item.children[0].name}}</span>
            </el-menu-item>
          </template>
        </el-menu>
        <!--<el-menu :default-active="defaultActiveIndex" router :collapse="collapsed" @select="handleSelect">-->
        <!--<template v-for="(item,index) in $router.options.routes" v-if="item.menuShow">-->
        <!--<el-submenu v-if="!item.leaf" :index="index+''">-->
        <!--<template slot="title"><i :class="item.iconCls"></i><span slot="title">{{item.name}}</span></template>-->
        <!--<el-menu-item v-for="term in item.children" :key="term.path" :index="term.path" v-if="term.menuShow"-->
        <!--:class="$route.path==term.path?'is-active':''">-->
        <!--<i :class="term.iconCls"></i><span slot="title">{{term.name}}</span>-->
        <!--</el-menu-item>-->
        <!--</el-submenu>-->
        <!--<el-menu-item v-else-if="item.leaf&&item.children&&item.children.length" :index="item.children[0].path"-->
        <!--:class="$route.path==item.children[0].path?'is-active':''">-->
        <!--<i :class="item.iconCls"></i><span slot="title">{{item.children[0].name}}</span>-->
        <!--</el-menu-item>-->
        <!--</template>-->
        <!--</el-menu>-->
      </aside>
    </el-col>
    <el-col :span="21" style='height: 94%;background-color: #f4f4f4'>
      <!--头部-->
      <el-row :span="24" class="topbar-wrap">
        <div class="ui-header-wrap clearfix J-headerWrap" style='margin-left: 9%;margin-right: 5%;'>
          <el-col :span='16' class="feature clearfix">
            <a href="/" class="link active">全部</a>
            <a href="/" class="link ">联系人</a>
            <a href="/" class="link ">表单</a>
            <a href="/" class="link ">邮件</a>
            <a href="/" class="link ">短信</a>
            <a href="/" class="link ">微信</a>
            <a href="/" class="link ">系统设置</a>
          </el-col>
          <el-col :span='8' class="ui-header-other J-headerOther" style="right: 0;">
            <!--<div class="lang-select">-->
              <!--<div class="ui-langSelect J-ui-langSelect">-->
                <!--<div class="wrap">-->
                  <!--<div class="select J-select">-->
                    <!--<span>简体中文</span>-->
                    <!--<i class="lang-icon"></i>-->
                    <!--<i class="select-icon"></i>-->
                  <!--</div>-->

                  <!--<div class="options">-->
                    <!--<p data-lang="zh_CN" class="option J-option">简体中文</p>-->
                    <!--<p data-lang="en_US" class="option J-option">English</p>-->
                  <!--</div>-->
                <!--</div>-->
              <!--</div>-->
            <!--</div>-->

            <div class="search">
              <div class="ui-search">
                <form class="form J-form" method="get" action="/search">
                  <input id="kw" class="kw" name="search_key" type="text" placeholder="输入关键字搜索文章">
                  <button title="搜索" class="btn btn-submit iconfont-search J-submitBtn" type="submit"></button>
                </form>
              </div>
            </div>
          </el-col>
        </div>
      </el-row>

      <!--中间-->
      <el-row :span="24" class="main">
        <!--右侧内容区-->
        <section class="content-container">
          <div class="grid-content bg-purple-light">
            <el-col :span="24" class="content-wrapper">
              <transition name="fade" mode="out-in">
                <router-view></router-view>
              </transition>
            </el-col>
          </div>
        </section>
      </el-row>
      <el-row :span="24" class="foot">
        <!--底部-->
        <div class="ui-footer J-ui-footer">
          <div class="wrap">
            <ul class="list clearfix">
              <li class="item">客服电话：15711187712</li>
              <li class="item line"></li>
              <li class="item">QQ：1803264906</li>
              <li class="item line"></li>
              <li class="item">邮箱：service@mikecrm.com</li>

              <li class="item line"></li>
              <li class="item item-link">
                <a target="_blank" href="http://cn.mikecrm.com/kytc1TK">合作投稿</a>
              </li>
              <li class="item line"></li>
              <li class="item item-link">
                <a target="_blank" href="http://cn.mikecrm.com/UrbQiTI">违规举报</a>
              </li>

              <li class="item line"></li>
              <li class="item item-share clearfix">
                <span class="text-tip">关注麦客: </span>
                <a class="footer-icon-wrap" href="http://weibo.com/u/3764069423" target="_blank">
                  <i class="footer-icon weibo"></i>
                </a>
                <span class="footer-icon-wrap J-share-wx">
          <i class="footer-icon wx"></i>
        </span>
              </li>
              <li class="item item-beian">
                <span class="beian">京ICP备15000327号</span>
              </li>
            </ul>
          </div>
        </div>
      </el-row>
    </el-col>

  </el-row>
</template>

<script>
  import {bus} from '../bus.js'
  import API from '../api/api_user';
  import ElRow from "element-ui/packages/row/src/row";

  export default {
    components: {ElRow},
    name: 'home',
    created(){
      bus.$on('setNickName', (text) => {
        this.nickname = text;
      })

      bus.$on('goto', (url) => {
        if (url === "/login") {
          localStorage.removeItem('access-user');
        }
        this.$router.push(url);
      })
    },
    data () {
      return {
        defaultActiveIndex: "0",
        nickname: '',
        collapsed: false,
      }
    },
    methods: {
      handleSelect(index){
        this.defaultActiveIndex = index;
      },
      //折叠导航栏
      // collapse: function () {
      //   this.collapsed = !this.collapsed;
      // },
      jumpTo(url){
        this.defaultActiveIndex = url;
        this.$router.push(url); //用go刷新
      },
      logout(){
        let that = this;
        this.$confirm('确认退出吗?', '提示', {
          confirmButtonClass: 'el-button--warning'
        }).then(() => {
          //确认
          that.loading = true;
          API.logout().then(function (result) {
            that.loading = false;
            localStorage.removeItem('access-user');
            that.$router.go('/login'); //用go刷新
          }, function (err) {
            that.loading = false;
            that.$message.error({showClose: true, message: err.toString(), duration: 2000});
          }).catch(function (error) {
            that.loading = false;
            console.log(error);
            that.$message.error({showClose: true, message: '请求出现异常', duration: 2000});
          });
        }).catch(() => {});
      }
    },
    mounted() {
      let user = localStorage.getItem('access-user');
      if (user) {
        user = JSON.parse(user);
        this.nickname = user.nickname || '';
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .container {
    position: absolute;
    top: 0px;
    bottom: 0px;
    width: 100%;

    .topbar-wrap {
      height: 50px;
      line-height: 50px;
      background: #ffffff;
      padding: 0px;

      .topbar-btn {
        color: #fff;
      }
      /*.topbar-btn:hover {*/
      /*background-color: #4A5064;*/
      /*}*/
      .topbar-title {
        float: left;
        text-align: left;
        width: 200px;
        padding-left: 10px;
        border-left: 1px solid #000;
      }
      .topbar-account {
        float: right;
        padding-right: 12px;
      }
      .userinfo-inner {
        cursor: pointer;
        color: #fff;
        padding-left: 10px;
      }
    }
    .margin-beside{
      margin-right: 20%;
      margin-left: 8%;
    }
    .main {
      /*display: -webkit-box;*/
      /*display: -webkit-flex;*/
      /*display: -ms-flexbox;*/
      /*display: flex;*/
      /*position: relative;*/
      /*background-color: #f4f4f4;*/
      /*top: 50px;*/
      height: 100%;
      /*bottom: 0px;*/
      overflow: hidden;
    }
    .ui-footer{
      height: 50px;
      background: #fff;
      border-top: 1px solid #e8e8e8;
      box-sizing: border-box;
      font-size: 13px;
      color: #818e99;
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      .list{
        display: inline-block;
        line-height: 15px;
        margin-top: 18px;
        list-style: none;
      }
      .line {
        width: 1px;
        height: 11px;
        font-size: 0;
        line-height: 11px;
        background: #c1c6cb;
        margin: 0 16px;
        margin-top: 1px;
      }
      .item {
        float: left;
      }

      .wrap{
        text-align: center;
      }
    }

    aside {
      min-width: 50px;
      background: #162a42;
      &::-webkit-scrollbar {
        display: none;
      }

      &.showSidebar {
        overflow-x: hidden;
        overflow-y: auto;
        height: 100%;
      }
      .topbar-logo {
        width: 100%;
        height: 50px;
        line-height: 50px;
      }
      .topbar-logo img {
        margin-top: 5%;
        margin-left: 20%;
      }
      .el-menu {
        height: 100%; /*写给不支持calc()的浏览器*/
        height: -moz-calc(100% - 80px);
        height: -webkit-calc(100% - 80px);
        height: calc(100% - 80px);
        border-radius: 0px;
        background-color: #333744;
        border-right: 0px;
      }

      .el-submenu .el-menu-item {
        min-width: 60px;
      }
      .el-menu {
        width: 100%;
      }
      .el-menu--collapse {
        width: 60px;
      }

      .el-menu .el-menu-item, .el-submenu .el-submenu__title {
        height: 46px;
        line-height: 46px;
      }

      .el-menu-item:hover, .el-submenu .el-menu-item:hover, .el-submenu__title:hover {
        background-color: #7ed2df;
      }
    }

    .menu-toggle {
      background: #4A5064;
      text-align: center;
      color: white;
      height: 26px;
      line-height: 30px;
    }

    .content-container {
      /*background: #f4f4f4;*/
      flex: 1;
      /*overflow-y: auto;*/
      padding-bottom: 1px;

      .content-wrapper {
        /*background-color: #f4f4f4;*/
        height: 100%;
        width:100%;
        box-sizing: border-box;
      }
    }
  }
</style>
