<template>
  <div class="header">
    <div class="content-wrapper">
        <div class="avatar">
          <img width="64" height="64" :src="seller.avatar">
        </div>
        <div class="content">
          <div class="title">
            <span class="brand"></span>
            <span class="name">{{seller.name}}</span>
          </div>
          <div class="description">
            {{seller.description}}/{{seller.deliveryTime}}分钟送达
          </div>
          <div v-if="seller.supports" class="support">
            <span class="icon" :class="classMap[seller.supports[0].type]"></span>
            <span class="text">{{seller.supports[0].description}}</span>
          </div>
        </div>
        <div v-if="seller.supports" class="support-count" @click="showDetail">
          <span class="count">{{seller.supports.length}}个</span>
          <i class="icon-keyboard_arrow_right"></i>
        </div>
    </div>
    <div class="bulletin-wrapper" @click="showDetail">
      <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
      <i class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img :src="seller.avatar" width="100%" height="100%">
    </div>
    <div class="detail" v-show="detailShow"></div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
      seller: {

      }
  },
  data() {
    return {
        detailShow: false
    }
  },
  methods: {
    showDetail: function () {
      this.detailShow = true;
    }
  },
  created() {
      this.classMap = ['decrease', 'discount', 'special', 'guarantee', 'invoice'];
  }
};
</script>

<style type="text/css">
  .header {
    position: relative;
    overflow: hidden;
    color: #ffffff;
    background: rgba(7, 17, 27, 0.5);
  }

  .content-wrapper {
    position: relative;
    padding: 24px 12px 18px 24px;
    font-size: 0;
  }

  .avatar, .content {
    display: inline-block;
  }

  .avatar {
    vertical-align: top;
  }

  .avatar img {
    border-radius: 2px;
  }

  .content {
    margin-left: 16px;
  }

  .title {
    margin: 2px 0 8px 0;
  }

  .brand {
    display: inline-block;
    vertical-align: top;
    width: 30px;
    height: 18px;
    background-image: url("brand@2x.png");
    background-size: 30px 18px;
    background-repeat: no-repeat;
  }

  .name {
    margin-left: 6px;
    color: rgb(255, 255, 255);
    font-size: 16px;
    line-height: 18px;
  }

  .description {
    margin-bottom: 10px;
    line-height: 12px;
    font-size: 12px;
  }

  .support {

  }

  .text {
    vertical-align: top;
    line-height: 12px;
    font-size: 10px;
  }

  .icon {
    display: inline-block;
    width: 12px;
    height: 12px;
    margin-right: 4px;
    background-size: 12px 12px;
    background-repeat: no-repeat;
  }

  .decrease {
    background-image: url("decrease_1@2x.png");
  }

  .discount {
    background-image: url("discount_1@2x.png");
  }

  .guarantee {
    background-image: url("guarantee_1@2x.png");
  }

  .invoice {
    background-image: url("invoice_1@2x.png");
  }

  .special {
    background-image: url("special_1@2x.png");
  }

  .support-count {
    position: absolute;
    right: 12px;
    bottom: 20px;
    padding: 0 8px;
    height: 24px;
    line-height: 24px;
    border-radius: 14px;
    background: rgba(0, 0, 0, 0.2);
    text-align: center;
  }

  .count, .icon-keyboard_arrow_right {
    font-size: 10px;
  }

  .bulletin-wrapper {
    background-color: rgba(7, 17, 27, 0.2);
    height: 28px;
    line-height: 28px;
    padding: 0 22px 0 12px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .bulletin-title {
    display: inline-block;
    vertical-align: top;
    margin-top: 8px;
    width: 22px;
    height: 12px;
    background-image: url("bulletin@2x.png");
    background-size: 22px 12px;
    background-repeat: no-repeat;
  }

  .bulletin-text {
    vertical-align: top;
    margin: 0 4px;
    font-size: 10px;
  }

  .background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    filter: blur(10px);
  }

  .detail {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;
    height: 100%;
    overflow: auto;
    background: rgba(7, 17, 27, 0.8);
    filter: blur(10px);
  }

</style>
