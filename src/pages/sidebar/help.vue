<template>
  <div class="help">
      <div class="title">
          <span>FAQ</span>
      </div>
      <div class="questions">
          <div class="setItem" :class="showQuestion1?'active':''" @click="showQuestion1=!showQuestion1">
            <input type="text" value="Question 1" placeholder-style="color:black" disabled="true">
            <image :src="showQuestion1?'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-up.png':'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png'"></image>
            <text v-if="showQuestion1">if questions 1 too long for this area?\n</text>
            <text v-if="showQuestion1">Answer</text>
         </div>
         <div class="setItem" :class="showQuestion2?'active':''" @click="showQuestion2=!showQuestion2">
            <input type="text" value="Question 2" placeholder-style="color:black" disabled="true">
            <image :src="showQuestion2?'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-up.png':'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png'"></image>
            <text v-if="showQuestion2">if questions 2 too long for this area?\n</text>
            <text v-if="showQuestion2">Answer</text>
         </div>
         <div class="setItem" :class="showQuestion3?'active':''" @click="showQuestion3=!showQuestion3">
            <input type="text" value="Question 3" placeholder-style="color:black" disabled="true">
            <image :src="showQuestion3?'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-up.png':'../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png'"></image>
            <text v-if="showQuestion3">if questions 3 too long for this area?\n</text>
            <text v-if="showQuestion3">Answer</text>
         </div>
      </div>
  </div>
</template>

<script>
export default {
    name:"help",
    data() {
        return {
            showQuestion1:false,
            showQuestion2:false,
            showQuestion3:false,
        }
    },
}
</script>

<style lang="less">
.help{
    margin: 50rpx;
    .title{
        margin: 50rpx 0;
        font-size: 40rpx;
        font-weight: 600;
    }
    .questions{
        .setItem{
            position: relative;
            image{
                width: 50rpx;
                height: 50rpx;
                position: absolute;
                top: -10rpx;
                right: 10rpx;
                transform: translate(-50%,60%);
            }
            span{
                font-size: 30rpx;
            }
            input{
                display: flex;
                justify-content: flex-start;
                align-items: center;
                border: 3rpx solid #c6cbcc;   
                border-radius: 50rpx;
                width: 100%;
                height: 85rpx;
                margin: 25rpx 0 10rpx;
                padding-left: 35rpx;
                box-sizing: border-box;
                font-size: 30rpx;
            }
        }
    }
}
.active{
    width: 100%;
    height: 220rpx;
    background-color: rgb(154, 240, 255);
    border-radius: 50rpx;
    transition: 100ms;
    input{
        width: 100%;
        height: 85rpx;
        background-color: white;
    }
    text{
        height: 100%;
        width: 100%;
        font-size: 28rpx;
        padding-left: 50rpx;
    }
}
</style>