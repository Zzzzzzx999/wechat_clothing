<template>
<div class="s">
    <!-- 置顶栏 -->
    <div class="functionalArea">
        <div class="menu">
            <image id="menu" src="../../static/icon/功能.png"></image>
            <image id="shoppingbag" src="../../static/icon/FeatherIconSet/Feather_Miscellaneous/shopping-bag.png"></image>
        </div>
    </div>
    <div class="setting">
      <div class="title">
          <span>My Address</span>
      </div>
      <div class="item">
         <div class="setItem">
             <text>Home: 4043 Willis Avenue, TRAPPER CREEK, 99638</text>
            <image src="../../static/icon/编辑.png"></image>
         </div>
      </div>
      <div class="item">
         <div class="setItem">
             <text>Work: 1923 Meadowbrook Mall Road, Gardena,CA, 90248 </text>
            <image src="../../static/icon/编辑.png"></image>
         </div>
      </div>
      <div class="button">
        <button @click="btnPath('./myAddress')">ADD NEW ADDRESS</button>
      </div>
  </div>
  
</div>
  
</template>

<script>
export default {
    name:"myAddressList",
    data() {
        return {
            
        }
    },
    methods: {
        btnPath(a){
            wx.redirectTo({url:a})
        }
    },
}
</script>

<style lang="less">
    .s{
        height: 100vh;
        display: flex;
        flex-flow: column;
    }
    .functionalArea{
        border-bottom: 3rpx solid rgb(221, 218, 218);
        .menu{
            display: flex;
            flex-flow: row nowrap;
            justify-content: space-between;
            align-items: center;
            padding: 20rpx 50rpx;
            width: 100%;
            box-sizing: border-box;
            #menu{
                width: 50rpx;
                height: 50rpx;
            }
            #shoppingbag{
                width: 50rpx;
                height: 50rpx;
            }
        }
    }
    .setting{
        margin: 50rpx;
        flex-grow: 1;
        position: relative;
        .title{
            font-size: 43rpx;
            font-weight: 600;
            margin: 30rpx 0;
        }
        .setItem{
            display: flex;
            justify-content: space-between;
            align-items: center;
            image{
                width: 50rpx;
                height: 50rpx;
            }
            text{
                // flex-grow: 1;
                padding-right: 30rpx;
                word-break: break-all;
                color: rgba(0, 0, 0, 0.671);
            }
        }
        .item{
            margin: 50rpx 0;
            text{
                width: 570rpx;
                font-size: 34rpx;
            }
        }
        button{
            // margin-top: 500rpx;
            background-color: rgb(20, 196, 228);
            border-radius: 50rpx;
            color: white;
            font-size: 35rpx;
            font-weight: 500;
            height: 100rpx;
            vertical-align: center;
            text-align: center;
            line-height: 100rpx;
        }
        .button{
            width: 100%;
            position: absolute;
            bottom: 150rpx;
        }
    }
</style>