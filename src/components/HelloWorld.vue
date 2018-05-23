<template>
   <div class="tmpl">
        <!-- 1.0 页面头，菜单导航代码 -->
        <div id="header" class="header">
            <div class="head-top">
                <div class="section">
                    <div class="left-box">
                        <span>嘎嘎嘎比卡丘</span>
                        <a target="_blank" href="#"></a>
                        <a target="_blank" href="#"></a>
                    </div>
                    <div id="menu" class="right-box">
                        <a href="/login.html">登录</a>
                        <a href="/register.html">注册</a>
                        <strong>|</strong>
                        <!--<a href="/content/contact.html"><i class="iconfont icon-phone"></i>联系我们</a>
                         <a href="/cart.html"><i class="iconfont icon-cart"></i>购物车(<span id="shoppingCartCount"><script type="text/javascript" src="/tools/submit_ajax.ashx?action=view_cart_count"></script></span>)</a>-->
                    </div>
                </div>
            </div>
            <div class="head-nav">
                <div class="section">
                    <!-- <div class="logo">
                                       <a href="/index.html"><img width="230px" height="70px" src="/templates/main/images/logo.png" /></a>
                                   </div>-->
                    <div id="menu2" class="nav-box menuhd">
                        <ul>
                            <li v-for="item in menuList"
                            :key="item.index"
                            :class="item.class"
                            >
                            <a :href="item.path">{{item.title}}</a>
                            </li>
                            <li>
                               <router-link to="/site/goodslist">
                                    购物商城
                                </router-link>
                            </li>
                        </ul>
                    </div>
                    <div class="search-box">
                        <div class="input-box">
                            <input id="keywords" name="keywords" type="text" onkeydown="if(event.keyCode==13){SiteSearch('/search.html', '#keywords');return false};"
                                placeholder="输入关健字" x-webkit-speech="">
                        </div>
                        <a href="javascript:;" onclick="SiteSearch('/search.html', '#keywords');">
                            <i class="iconfont icon-search"></i>
                        </a>
                    </div>
                </div>
            </div>
        </div>
        <!-- 轮播图 -->
        <slider></slider>  
        <!-- 使用wow.js来完成动画的渲染 -->
        <homewow></homewow>

        <!-- 2.0 路由的占位符 -->
        <router-view></router-view>
    </div>
</template>

<script>
import slider from './slider'
import homewow from './homewow'
$(function() {
  $("#menu2 li a").wrapInner('<span class="out"></span>');
  $("#menu2 li a").each(function() {
    $('<span class="over">' + $(this).text() + "</span>").appendTo(this);
  });

  $("#menu2 li a").hover(
    function() {
      $(".out", this)
        .stop()
        .animate({ top: "48px" }, 300); // move down - hide
      $(".over", this)
        .stop()
        .animate({ top: "0px" }, 300); // move down - show
    },
    function() {
      $(".out", this)
        .stop()
        .animate({ top: "0px" }, 300); // move up - show
      $(".over", this)
        .stop()
        .animate({ top: "-48px" }, 300); // move up - hide
    }
  );
});

export default {
  name: "HelloWorld",
  components: {
      slider,
      homewow
  },
  data() {
    return {
      menuList: [
        {
          path: "/index.html",
          title: "首页",
          class: "index"
        },
        {
          path: "/news.html",
          title: "游乐场",
          class: "news"
        },
        {
          path: "/photo.html",
          title: "一日游",
          class: "photo"
        },
        {
          path: "/video.html",
          title: "温泉",
          class: "video"
        },
        {
          path: "/down.html",
          title: "赏花",
          class: "down"
        }
      ]
    };
  },
  methods: {},
  mounted() {
    //打印这个$就知道有没有配置到jq了
    // console.log($)
  }
};
</script>

<style scoped lang="less">
/* 为了解决统一导入elemenui的样式,所以要放到layout.vue */
/* 导入样式的格式  @import url() */
@import url("../../static/elementuiCss/index.css");
.tmpl {
  overflow: hidden;
}
</style>
