<template>
  <div class="featured" :class="{'home-hide':showDialog}" @touchstart="touchstart" @touchmove="touchmove" @click="showDialog = false">
        <!-- 置顶栏 -->
        <div class="functionalArea" @click.stop>
            <div class="menu">
                <image id="menu" @click="showDialog = true" src="../static/icon/功能.png"></image>
                <image id="shoppingbag" src="../static/icon/FeatherIconSet/Feather_Controls/filter.png"></image>
            </div>
        </div>
        <div class="featuredbox">
            <div class="featuredHeader">
                <span id="title">Featured For You</span>
            </div>
            <div class="featuredProducts">
                <!-- 待修改 -->
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                    <span>Red Overalls</span><br>
                    <span id="price">$39</span>
                    <span id="lastPrice">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                    <span>Pink Fur Coat</span><br>
                    <span id="price">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                    <span>Red Overalls</span><br>
                    <span id="price">$39</span>
                    <span id="lastPrice">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                    <span>Pink Fur Coat</span><br>
                    <span id="price">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                    <span>Red Overalls</span><br>
                    <span id="price">$39</span>
                    <span id="lastPrice">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                    <span>Pink Fur Coat</span><br>
                    <span id="price">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                    <span>Red Overalls</span><br>
                    <span id="price">$39</span>
                    <span id="lastPrice">$59</span>
                </div>
                <div class="product">
                    <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                    <span>Pink Fur Coat</span><br>
                    <span id="price">$59</span>
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
    name:'featured',
    components:{zzc},
    data() {
        return {
            // 导航栏
            tab_homePage:false,
            tab_category:false,
            tab_feature:true,
            tab_my:false,
            // 侧滑栏
            start_clientX:0, //手指触摸开始
            end_clientX:0, //手指触摸结束
            windowWidth:wx.getSystemInfoSync().windowWidth, //获取屏幕宽度
            translate:'',
            showDialog: false,
        }
    },
    mounted() {
        console.log(123);
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
    // 主页
    .featured .functionalArea{
        width: 770rpx;
        border-bottom: 3rpx solid rgb(221, 218, 218);
    }
    .featured .functionalArea .menu{
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        padding: 20rpx 50rpx;
        width: 100%;
        box-sizing: border-box;
    }
    .featured .functionalArea .menu #menu{
        width: 50rpx;
        height: 50rpx;
    }
    .featured .functionalArea .menu #shoppingbag{
        width: 50rpx;
        height: 50rpx;
    }

    //中间
    .featured .featuredbox{
        margin: 30rpx 50rpx;
        width: 652rpx;
    }
    .featured .featuredbox .featuredHeader{
        display: flex;
        flex-flow: row nowrap;
        justify-content: flex-start;
        align-items: center;
        #title{
            font-size: 40rpx;
            font-weight: 600;
            margin: 20rpx 0;
        }
    }

    .featured .featuredbox .featuredProducts{
        display: flex;
        justify-content:space-between;
        flex-flow: row wrap;
        margin-top: 25rpx;
        width: 100%;
        margin-bottom: 50rpx;
        padding-bottom: 150rpx;
    }
    .featured .featuredbox .featuredProducts .product{
        width: 43.5%;
        height: 420rpx;
    }
    .featured .featuredbox .featuredProducts .product image{
        width: 100%;
        height: 63%;
        border-radius: 20rpx;
        margin: 10rpx 0;
    }
    .featured .featuredbox .featuredProducts .product span{
        font-size: 32rpx;
    }
    .featured .featuredbox .featuredProducts .product #price{
        font-size: 42rpx;
        font-weight: 900;
    }
    .featured .featuredbox .featuredProducts .product #lastPrice{
        font-size: 32rpx;
        font-weight: 400;
        color: #dfdfdf;
        text-decoration:line-through;
        margin-left: 30rpx;
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