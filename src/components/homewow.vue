<template>
 <div id="container">
    <header>
      <h1>动画效果</h1>
    </header>
    <div id="main">
      <section class="wow fadeInDown" style="background-color: #f1c40f;"></section>
      <section class="wow pulse" style="background-color: #e74c3c;" data-wow-iteration="infinite" data-wow-duration="1500ms"></section>
      <section class="section--purple wow slideInRight" data-wow-delay="2s"></section>
      <section class="section--blue wow bounceInLeft" data-wow-offset="300"></section>
      <section class="section--green wow slideInLeft" data-wow-duration="4s"></section>
    </div>
  </div>

</template>



<script >
import lunbo from "../../src/base/wow.js";
// import '../../src/base/wow.js'
console.log(lunbo)
var wow = new lunbo.WOW({
  animateClass: "animated",
  offset: 100
});
wow.init();


export default {
  name: "homewow",
  data() {
    return {};
  },
  mounted() {}
};
</script>

<style lang="less" scoped>
@import url("../../static/site/css/animate.css");
// .wow:first-child {
//   visibility: hidden;
// }
h1 {
  font-size: 72px;
  line-height: 1.5;
  color: #2c3e50;
  font-weight: 100;
}

#container {
  width: 980px;
  margin: 0 auto;
}

section {
  height: 300px;
  margin: 60px 0;
}

.section--purple {
  background-color: #9b59b6;
}

.section--blue {
  background-color: #3498db;
}

.section--green {
  background-color: #2ecc71;
}

#main {
  text-align: center;
}

#more {
  margin: 20px auto 48px;
}
</style>

