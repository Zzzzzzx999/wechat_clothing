<template>
    <div class="content" :class="{'home-hide':showDialog}" @touchstart="touchstart" @touchmove="touchmove" @click="showDialog = false">
        <div class="functionalArea" @click.stop>
            <div class="menu">
                <image id="menu" @click="showDialog = true" src="../static/icon/功能.png"></image>
                <image id="shoppingbag" @click="btnPath('./featured')" src="../static/icon/FeatherIconSet/Feather_Miscellaneous/shopping-bag.png"></image>
            </div>
        </div>
        <div class="category">
            <span id="title">Category</span>
            <div class="categoryItem">
                <image mode="aspectFill" src="https://img1.baidu.com/it/u=3405660659,4084470157&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=280"></image>
                <span>WOMAN</span>
            </div>
            <div class="categoryItem">
                <image mode="aspectFill" src="https://img1.baidu.com/it/u=661657988,2483268463&fm=253&fmt=auto&app=120&f=GIF?w=500&h=280"></image>
                <span>MAN</span>
            </div>
            <div class="categoryItem">
                <image mode="aspectFill" src="https://img0.baidu.com/it/u=1802279795,990858685&fm=253&fmt=auto&app=138&f=PNG?w=5000&h=280"></image>
                <span>KIDS</span>
            </div>
        </div>
        <!-- 侧滑栏 -->
        <zzc :showDialog=showDialog></zzc>
        <!-- 导航栏 -->
        <div class="tabbar" v-if="!showDialog">
            <div class="tabItem" @click="btnPath('./homePage')">
                <image :src="tab_homePage?'../static/icon/首页(1).png':'../static/icon/首页.png'"></image>
            </div>
            <div class="tabItem" @click="btnPath('./category')">
                <image :src="tab_category?'../static/icon/商圈(1).png':'../static/icon/商圈.png'"></image>
            </div>
            <div class="tabItem" @click="btnPath('./featured')">
                <image :src="tab_feature?'../static/icon/收藏(1).png':'../static/icon/收藏.png'"></image>
            </div>
            <div class="tabItem" @click="btnPath('./my')">
                <image :src="tab_my?'../static/icon/我的关注(1).png':'../static/icon/我的关注.png'"></image>
            </div>
        </div>
    </div>
</template>

<script>
import zzc from './zzc.vue'
export default {
    name:'category',
    components:{zzc},
    data() {
        return {
            // 导航栏
            tab_homePage:false,
            tab_category:true,
            tab_feature:false,
            tab_my:false,
            // 侧滑栏
            start_clientX:0, //手指触摸开始
            end_clientX:0, //手指触摸结束
            windowWidth:wx.getSystemInfoSync().windowWidth, //获取屏幕宽度
            translate:'',
            showDialog: false,
        }
    },
    methods: {
        btnPath(a){
            wx.redirectTo({url:a})
        },
        touchstart(e){
            // console.log(e);
            this.start_clientX = e.changedTouches[0].clientX
        },
        touchmove(e){
            if (e.changedTouches[0].clientX - this.start_clientX > 100) {
                this.showDialog = true
            } else {
                // this.showDialog = false
            }
        },
    },
}
</script>

<style lang="less">
    .content .functionalArea{
        width: 770rpx;
        border-bottom: 3rpx solid rgb(221, 218, 218);
    }
    .content .functionalArea .menu{
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        padding: 20rpx 50rpx;
        width: 100%;
        box-sizing: border-box;
    }
    .content .functionalArea .menu #menu{
        width: 50rpx;
        height: 50rpx;
    }
    .content .functionalArea .menu #shoppingbag{
        width: 50rpx;
        height: 50rpx;
    }

    .category{
        display: flex;
        flex-flow: column nowrap;
        margin: 30rpx 50rpx;
        span{
            font-size: 40rpx;
            font-weight: 600;
            margin: 20rpx 0;
        }
        .categoryItem{
            height: 210rpx;
            width: 100%;
            margin: 20rpx 0;
            position: relative;
            image{
                width: 100%;
                height: 100%;
                border-radius: 15rpx;
            }
            span{
                position: absolute;
                bottom: 10rpx;
                left: 30rpx;
                color: white;
                font-size: 32rpx;
                font-weight: 600;
            }
        }
    }
    //底部导航栏 
    .tabbar{
        display: flex;
        position: fixed;
        flex-flow: row nowrap;
        justify-content: space-around;
        // align-items: center;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 10vh;
        background-color: #fff;
        border: 3rpx solid rgba(223, 219, 219, 0.932);
        border-top-left-radius: 40rpx;
        border-top-right-radius: 40rpx;
        padding-top: 30rpx;
        .tabItem{
            width: 25%;
            padding-left: 45rpx;
            image{
                width: 60rpx;
                height: 60rpx;
            }
        }
    }
</style>