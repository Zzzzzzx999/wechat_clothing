<template>
    <div class="content" :class="{'home-hide':showDialog}" @touchstart="touchstart" @touchmove="touchmove" @click="showDialog = false">
        <!-- 置顶栏 -->
        <div class="functionalArea" @click.stop>
            <div class="menu">
                <image id="menu" @click="showDialog = true" src="../static/icon/功能.png"></image>
                <image id="shoppingbag" @click="btnPath('./featured')" src="../static/icon/FeatherIconSet/Feather_Miscellaneous/shopping-bag.png"></image>
            </div>
        </div>
        <!-- 文本 -->
        <div class="textContent">
            <div class="title">
                <span>Wish List</span>
            </div>
            <div class="cards">
                <div class="card" v-if="showCard1">
                    <div class="photo">
                        <image mode="aspectFill" src="https://img0.baidu.com/it/u=4240677782,2919367140&fm=253&fmt=auto&app=138&f=JPEG?w=333&h=499"></image>
                    </div>
                    <div class="detail">
                        <text id="name" decode="true" class="detail">Calf-length Wrap Dress\n</text>
                        <text decode="true" class="detail">Price：39,99$\n\nLowest Price for 6 month：34,99$</text>
                    </div>
                    <div class="like">
                        <image src="../static/icon/导航_收藏_已收藏.png" @click="showCard1=false"></image>
                    </div>
                </div>
                <div class="card" v-if="showCard2">
                    <div class="photo">
                        <image mode="aspectFill" src="https://img1.baidu.com/it/u=1826734950,108253847&fm=253&fmt=auto&app=138&f=JPEG?w=459&h=500"></image>
                    </div>
                    <div class="detail">
                        <text id="name" decode="true" class="detail">Puff-sleeved Blouse\n</text>
                        <text decode="true" class="detail">Price：64,50$\n\nLowest Price for 6 month：54,99$</text>
                    </div>
                    <div class="like">
                        <image src="../static/icon/导航_收藏_已收藏.png" @click="showCard2=false"></image>
                    </div>
                </div>
            </div>
        </div>
        <!-- 侧滑栏 -->
        <zzc :showDialog=showDialog></zzc>
        <!-- 导航栏 -->
        <div class="tabbar" v-show="!showDialog">
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
    name:'my',
    components:{zzc},
    data() {
        return {
            // 导航栏
            tab_homePage:false,
            tab_category:false,
            tab_feature:false,
            tab_my:true,
            //Wish card
            showCard1:true,
            showCard2:true,
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
    //置顶栏
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


    //内容区
    .textContent{
        margin: 50rpx;
    }
    .textContent .title{
        font-weight: 600;
        font-size: 43rpx;
        margin: 50rpx 0;
    }
    .textContent .cards{
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-flow: column nowrap;
    }
    .textContent .cards .card{
        width: 100%;
        height: 150rpx;
        margin: 15rpx 0;
        border: 1rpx solid #dfdfdf;
        border-radius: 15rpx;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-flow: row nowrap;
        padding: 15rpx 0;
        word-break: break-all;
    }
    .textContent .cards .card .photo{
        width: 26%;
        height: 130rpx;
        text-align: center;
    }
    .textContent .cards .card .photo image{
        width: 120rpx;
        height: 120rpx;
        border-radius: 50%;
    }
    .textContent .cards .card .detail{
        flex-grow: 1;
        height: 130rpx;
        font-size: 24rpx;
        position: relative;
        font-family: 500;
    }
    .textContent .cards .card .detail #name{
        font-weight: 600;
    }
    .textContent .cards .card .detail #lowestPrice{
        height: 50rpx;
        position: absolute;
        bottom: 0;
    }
    .textContent .cards .card .like{
        width: 14%;
        height: 130rpx;
        align-items: flex-start;
        text-align: center;
    }
    .textContent .cards .card .like image{
        width: 60rpx;
        height: 60rpx;
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