<template>
  <div class="language">
        <div class="functionalArea">
            <div class="menu">
                <image id="menu" src="../../static/icon/功能.png"></image>
                <image id="shoppingbag" src="../../static/icon/FeatherIconSet/Feather_Miscellaneous/shopping-bag.png"></image>
            </div>
        </div>
        <div class="content">
            <div class="title">
                <span>Language</span>
            </div>
            <radio-group @change="radioChange">
                <label class="lan" v-for="(item,index) in items" :key="item.value">
                    <div class="lanItem">{{item}}</div>
                    <div class="radio" @click="btnCheck(index)">
                        <div :class="{'radio-active':index === itemsIndex}"></div>
                        <!-- <radio color="blue" :value="item.value" :checked="item=='English'"></radio> -->
                    </div>
                </label>
            </radio-group>
            <div class="button">
                <button @click="btnPath('../homePage')">DONE</button>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    name:'language',
    data() {
        return {
            itemsIndex: 0,
            items:['English','Turkish','Russian','French','German','Italian','Thai','Portuguese','Mandarin']
        }
    },

    methods: {
        btnCheck(index) {
            this.itemsIndex = index
        },
        btnPath(a){
            wx.redirectTo({url:a})
        }
    }
}
</script>

<style lang="less">
.language{
    height: 100vh;
    display: flex;
    flex-flow: column nowrap;
}

// 顶部功能区
.language .functionalArea{
    width: 770rpx;
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

// 文本内容
.language .content{
    flex-grow: 1;
    margin: 50rpx;
    position: relative;
    .title{
        font-size: 40rpx;
        font-weight: 600;
        letter-spacing: 3rpx;
        margin: 50rpx 0;
    }
    .lan{
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-flow: row nowrap;
        margin: 20rpx 0;
        font-size: 33rpx;
        font-weight: 400;
        letter-spacing: 2rpx;
        position: relative;
        .lanItem{
            flex-grow: 1;
        }
        .radio{
            width: 50rpx;
            height: 50rpx;
            // padding: 4rpx;
            position: relative;
            border: 4rpx solid #2b90af;
            border-radius: 50%;
            box-sizing: border-box;
        }
        .radio-active{
            width: 80%;
            height: 80%;
            background: #6bd3f3;
            border-radius: 50%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
        }   
    }
    .button{
        width: 100%;
        position: absolute;
        bottom: 200rpx;
    }
    button{
        background-color: rgb(20, 196, 228);
        border-radius: 50rpx;
        margin-top: 100rpx;
        color: white;
        font-size: 35rpx;
        font-weight: 500;
        height: 100rpx;
        vertical-align: center;
        text-align: center;
        line-height: 100rpx;
    }
}

</style>