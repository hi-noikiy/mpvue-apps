<template>
  <div class="admin-shop-info">
    <div class="shop_info">
      <img src="../../../static/jp.jpg" alt="" class="shop_img">
    </div>
    <div class="options">
      <p>店铺名字</p>
      <input type="text" placeholder="请填写店铺姓名">
    </div>
    <div class="options">
      <p>营业时间</p>
      <picker mode="time" :value="startTime" start="00:00" end="23:59" @change="startTimeChange" class="timeSelect">
        <view class="picker">开始时间：{{startTime}}</view>
      </picker>
      <picker mode="time" :value="endTime" start="00:00" end="23:59" @change="endTimeChange" class="timeSelect">
        <view class="picker">结束时间：{{endTime}}</view>
      </picker>
      <img src="../../../static/userImg.png" alt="">
    </div>
    <div class="options">
      <p>店铺类型</p>
      <checkbox-group @change="checkboxChange">
        <label class="checkbox" v-for="(v,i) in typeList" :key="i">
              <checkbox :value="v.value" :checked="v.checked" :disabled="v.disabled" color="#666" class="checkbox_info" />
              {{v.value}}
            </label>
      </checkbox-group>
    </div>
    <div class="options">
      <p>店铺地址</p>
      <picker mode="region" @change="regionChange" :value="region" :custom-item="customItem" class="citySelect">
        <view class="picker">
          {{region[0]}} {{region[1]}} {{region[2]}}
        </view>
      </picker>
      <img src="../../../static/userImg.png" alt="">
    </div>
    <div class="options">
      <p>详细地址</p>
      <input type="text" placeholder="详细地址，例1号楼2层201室">
    </div>
    <div class="options">
      <p>店铺简介</p>
      <input type="text" placeholder="请输入店铺简介24字以下" maxlength="24">
    </div>
    <div class="options">
      <p>联系电话</p>
      <input type="text" placeholder="请填写联系电话" maxlength="11">
    </div>
    <div class="options">
      <p>联系微信</p>
      <input type="text" placeholder="请填微信号">
    </div>
    <div class="btn_next">下一步</div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        region: ['点击选择', '', ''],
        customItem: '请选择',
        startTime: '00:00',
        endTime: '00:00',
        typeList: [{
            name: 'food',
            value: '餐饮类',
            checked: false,
            disabled: false
          },
          {
            name: 'other',
            value: '其它',
            checked: false,
            disabled: false
          },
        ]
      }
    },
    mounted() {},
    methods: {
      regionChange(e) {
        console.log(e)
        this.region = e.target.value;
      },
      startTimeChange(e) {
        this.startTime = e.target.value;
      },
      endTimeChange(e) {
        this.endTime = e.target.value;
      },
      checkboxChange: function(e) {
        console.log(e.target.value)
      }
    },
    components: {}
  }
</script>

<style lang="less">
  .admin-shop-info {
    height: 100%;
    background: #f5f5f5;
    overflow-x: hidden;
    .shop_info {
      display: flex;
      align-items: center;
      flex-direction: column;
      justify-content: center;
      padding: 40rpx 0;
      .shop_img {
        width: 140rpx;
        height: 140rpx;
        border-radius: 50%;
      }
    }
    .options {
      background: #fff;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      padding: 20rpx;
      border-bottom: 1rpx solid #e6e6e6;
      .checkbox {
        margin-right: 20rpx;
        font-size: 24rpx;
        color: #666;
        .checkbox_info {
          margin-right: 4rpx;
          transform: scale(.7);
        }
      }
      p {
        font-size: 24rpx;
        color: #333;
        width: 140rpx;
        text-align: left;
        transform: translateY(3rpx);
      }
      input {
        flex-grow: 1;
        font-size: 24rpx;
        color: #666;
      }
      .citySelect,
      .timeSelect {
        flex-grow: 1;
        color: #777;
        margin-right: 20rpx;
      }
      img {
        width: 50rpx;
        height: 50rpx;
        margin-left: 20rpx;
      }
    }
    .btn_next {
      background: skyblue;
      margin: 26rpx 20rpx;
      text-align: center;
      height: 80rpx;
      line-height: 80rpx;
      border-radius: 8rpx;
      color: #fff;
      font-size: 30rpx;
    }
  }
</style>
