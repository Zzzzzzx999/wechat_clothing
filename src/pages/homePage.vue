<template>
    <div class="home" :class="{'home-hide':showDialog}" @touchstart="touchstart" @touchmove="touchmove" @touchend="touchend">
        <!-- 主页 -->
        <div class="content">
            <div class="functionalArea">
                <div class="menu">
                    <!-- <image id="menu" src="../static/icon/FeatherIconSet/Feather_Menu/menu.png"></image> -->
                    <image id="menu" @click="showDialog = true" src="../static/icon/功能.png"></image>
                    <image id="shoppingbag" @click="btnPath('./featured')" src="../static/icon/FeatherIconSet/Feather_Miscellaneous/shopping-bag.png"></image>
                </div>
                <!-- <div class="goods">
                    <image src=""></image>
                </div> -->
            </div>
            <div class="search">
                <input type="text" placeholder="Search">
                <image src="../static/icon/Feather_qr code.png"></image>
            </div>
            <div class="collections">
                <span id="title">Collections</span>
                <scroll-view class="pageSectionSwiper" scroll-x="true">
                    <div class="pages">
                        <div class="pageItem">
                            <image mode="aspectFill" src="https://img0.baidu.com/it/u=1154249711,655486810&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500" alt="">
                            <span id="theme">SPRING</span>
                        </div>
                        <div class="pageItem">
                            <image mode="aspectFill" src="https://img1.baidu.com/it/u=2598906982,771980122&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500" alt="">
                            <span id="theme">WEDDING</span>
                        </div>
                        <div class="pageItem">
                            <image mode="aspectFill" src="https://img2.baidu.com/it/u=1325961303,69716533&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500" alt="">
                            <span id="theme">SUMMER</span>
                        </div>
                    </div>
                </scroll-view>
            </div>
            <div class="featured">
                <div class="featuredHeader">
                    <span id="title">Featured Products</span>
                    <div class="more">
                        <span @click="lookMore">More</span>
                    </div>
                </div>
                <div class="featuredProducts">
                    <div class="product" @click="btnPath('./detail')">
                        <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                        <span>Red Overalls</span><br>
                        <span id="price">$39</span>
                        <span id="lastPrice">$59</span>
                    </div>
                    <div class="product" @click="btnPath('./detail')">
                        <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                        <span>Pink Fur Coat</span><br>
                        <span id="price">$59</span>
                    </div>
                </div>
                <div class="featuredProducts">
                    <div class="product" @click="btnPath('./detail')">
                        <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F012403603dbb4e11013f3745780f90.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=a272b530f726b31259782e512df04ff1"></image>
                        <span>Red Overalls</span><br>
                        <span id="price">$39</span>
                        <span id="lastPrice">$59</span>
                    </div>
                    <div class="product" @click="btnPath('./detail')">
                        <image mode="aspectFill" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F0135b5603dbb4311013ef90fd48393.jpg%401280w_1l_2o_100sh.jpg&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656402430&t=4a72be4882e38e1159f256abdf3bb9cd"></image>
                        <span>Pink Fur Coat</span><br>
                        <span id="price">$59</span>
                    </div>
                </div>
            </div>
        </div>
        <!-- 遮罩层 -->
        <div class="mask" :class="{'mask-show':showDialog}" @click="showDialog = false">
            <div class="dialog" @click.stop>
                <div class="user">
                    <div class="userAvatar">
                        <image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc-ssl.duitang.com%2Fuploads%2Fblog%2F202107%2F26%2F20210726234456_59a73.thumb.1000_0.jpeg&refer=http%3A%2F%2Fc-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656506368&t=defc1517a72e00446a5a177c66196353"></image>
                        <div class="edit">
                            <image mode="aspectFill" src="../static/icon/FeatherIconSet/Feather_Controls/edit.png"></image>
                        </div>
                    </div>
                    <span>Welcome,{{username}}</span>
                </div>
                <div class="functionDoMain">
                    <div class="orders functionItem">
                        <image src="../static/icon/FeatherIconSet/Feather_Controls/clipboard.png"></image>
                        <span>Orders</span>
                    </div>
                    <div class="wishList functionItem" @click="btnPath('../pages/my')">
                        <image src="../static/icon/FeatherIconSet/Feather_Layout/list.png"></image>
                        <span>Wish List</span>
                    </div>
                    <div class="lastViewed functionItem">
                        <image src="../static/icon/FeatherIconSet/Feather_Controls/eye.png"></image>
                        <span>Last Viewed</span>
                    </div>
                    <div class="shippingAdress functionItem" @click="btnPath('../pages/sidebar/myAddressList')">
                        <image src="../static/icon/FeatherIconSet/Feather_Maps/map-pin.png"></image>
                        <span>Shipping Adress</span>
                    </div>
                    <div class="language functionItem" @click="btnPath('../pages/sidebar/language')">
                        <image src="../static/icon/FeatherIconSet/Feather_Miscellaneous/globe.png"></image>
                        <span>Language</span>
                    </div>
                    <div class="settings functionItem" @click="btnPath('../pages/sidebar/settings')">
                        <image src="../static/icon/FeatherIconSet/Feather_Miscellaneous/settings.png"></image>
                        <span>Settings</span>
                    </div>
                    <div class="help functionItem" @click="btnPath('../pages/sidebar/help')">
                        <image src="../static/icon/FeatherIconSet/Feather_Help/help-circle.png"></image>
                        <span>Help</span>
                    </div>
                </div>
                <div class="logOut functionItem" @click="logOut()">
                    <image src="../static/icon/FeatherIconSet/Feather_Login-Logout/log-out.png"></image>
                    <span>Log out</span>
                </div>
            </div>
        </div>
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
export default {
    name:'homePage',
    data() {
        return {
            autoplay: true, //是否自动切换
            interval: 2000, //自动切换时间间隔
            duration: 500,   //滑动动画时长,
            // 侧滑栏
            start_clientX:0, //手指触摸开始
            end_clientX:0, //手指触摸结束
            windowWidth:wx.getSystemInfoSync().windowWidth, //获取屏幕宽度
            display:'none',
            translate:'',
            showDialog: false,
            // 导航栏
            tab_homePage:true,
            tab_category:false,
            tab_feature:false,
            tab_my:false,
            // 用户信息
            username:'Efsan Izmirli',
        }
    },
    methods: {
        touchstart(e){
            console.log(e);
            this.start_clientX = e.changedTouches[0].clientX
        },
        touchmove(e){
            if (e.changedTouches[0].clientX - this.start_clientX > 100) {
                this.showDialog = true
            } else {
                // this.showDialog = false
            }
        },
        touchend(e){
            console.log(this.end_clientX);
        },
        lookMore(){
            console.log('More');
            wx.redirectTo({url:'./home'})
        },
        logOut(){
            wx.redirectTo({url:'./index/signIn'})
        },
        btnPath(a){
            wx.redirectTo({url:a})
        }
    }
}
</script>

<style lang="less">
    body{
        letter-spacing: 2rpx;
    }
    .home{
        transition: all .15s;
    }
    .home-hide{
        margin-left: 650rpx;
    }

    // 主页 
    .home .content{
        z-index: 1;
    }
    .home .content .functionalArea{
        width: 770rpx;
        border-bottom: 3rpx solid rgb(221, 218, 218);
    }
    .home .content .functionalArea .menu{
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        padding: 20rpx 50rpx;
        width: 100%;
        box-sizing: border-box;
    }
    .home .content .functionalArea .menu #menu{
        width: 50rpx;
        height: 50rpx;
    }
    .home .content .functionalArea .menu #shoppingbag{
        width: 50rpx;
        height: 50rpx;
    }

        // 主页:搜素框
    .home .content .search{
        width: 652rpx;
        height: 85rpx;
        margin: 25rpx 50rpx 0;
        padding: 0 35rpx;
        border: 3rpx solid rgb(99, 151, 155);
        border-radius: 15rpx;
        box-sizing: border-box;
        display: flex;
        align-items: center;
    }
    .home .content .search input{
        flex-grow: 1;
        height: 100%;
        font-size: 30rpx;
    }
    .home .content .search image{
        width: 50rpx;
        min-width: 50rpx;
        height: 50rpx;
        margin-left: 35rpx;
    }

    .home .content .collections{
        /* display: flex; */
        margin: 25rpx 0 25rpx 50rpx;
    }
    .home .content #title{
        font-weight: 600;
        font-size: 40rpx;
        flex-grow: 1;
    }
    .home .content .collections .pageSectionSwiper{
        display: inline-block;
        white-space: nowrap;
        margin: 20rpx 0;
    }
    .home .content .collections .pageSectionSwiper .pages{
        display: flex;
        flex-flow: row nowrap;
        box-shadow:0px 0px 30rpx 5rpx rgb(218, 216, 216);
    }
    .home .content .collections .pageSectionSwiper .pages .pageItem{
        width: 425rpx;
        height: 220rpx;
        margin-right: 30rpx;
        position: relative;
    }
    .home .content .collections .pageSectionSwiper .pages .pageItem #theme{
        position: absolute;
        color: white;
        bottom: 5%;
        left: 5%;
        font-size: 32rpx;
        font-weight: 600;
        z-index: 999;
    }
    .home .content .collections .pageSectionSwiper .pages .pageItem image{
        width: 425rpx;
        height: 220rpx;
        border-radius: 20rpx;
        filter: brightness(0.9);
        // box-shadow: 0px 0px 30rpx 10rpx rgb(218, 216, 216);
    }


    .home .content .featured{
        margin: 30rpx 50rpx 50rpx;
        padding-bottom: 130rpx;
        width: 652rpx;
    }
    .home .content .featured .featuredHeader{
        display: flex;
        flex-flow: row nowrap;
        justify-content: flex-start;
        align-items: center;
    }
    .home .content .featured .featuredHeader .more{
        display: flex;
        justify-content: center;
        align-items: center;
        height: 75rpx;
        width: 170rpx;
        border: 1rpx solid rgba(37, 169, 202, 0.829);
        // margin-left: 45rpx;
        border-radius: 20rpx;
        color: rgba(37, 169, 202, 0.829);
        font-size: 30rpx;
    }

    .home .content .featured .featuredProducts{
        display: flex;
        justify-content:space-between;
        flex-flow: row nowrap;
        margin-top: 25rpx;
        height: 420rpx;
        width: 100%;
        margin-bottom: 50rpx;
    }
    .home .content .featured .featuredProducts .product{
        width: 43.5%;
        height: 420rpx;
    }
    .home .content .featured .featuredProducts .product image{
        width: 100%;
        height: 63%;
        border-radius: 20rpx;
        margin: 10rpx 0;
    }
    .home .content .featured .featuredProducts .product span{
        font-size: 32rpx;
    }
    .home .content .featured .featuredProducts .product #price{
        font-size: 42rpx;
        font-weight: 900;
    }
    .home .content .featured .featuredProducts .product #lastPrice{
        font-size: 32rpx;
        font-weight: 400;
        color: #dfdfdf;
        text-decoration:line-through;
        margin-left: 30rpx;
    }

    // 遮罩层

    /* .bg {    
        display: none;    
        position: fixed;    
        top: 0%;    
        left: 70%;    
        width: 100%;    
        height: 100%;    
        background-color: black;    
        z-index: 1001;    
        -moz-opacity: 0.7;    
        opacity: 0.70;    
        transition:width 2s;  
        filter: alpha(opacity=70);    
    } */
    
    .mask{
        width: 100%;
        height: 100vh;
        background: rgba(0, 0, 0, .3);
        position: fixed;
        top: 0;
        left: -100vw;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        transition: all .15s;
        .dialog{
            width: 650rpx;
            height: 100%;
            background: #fff;
        }
    }
    .mask-show{
        left: 0;
    }
    
    // 底部导航栏
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

    // 侧滑栏
    .mask .dialog{
        position: relative;
        .user{
            display: flex;
            justify-content: center;
            align-items: flex-start;
            flex-flow: column nowrap;
            margin: 50rpx 50rpx 0;
            image{
                width: 120rpx;
                height: 120rpx;
                border-radius: 50%;
            }
            span{
                font-weight: 900;
                font-size: 42rpx;
                margin: 30rpx 0;
            }
            .userAvatar{
                position: relative;
                .edit{
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    position: absolute;
                    bottom: 0;
                    right: 0;
                    transform: translate(-5%,-20%);
                    width: 40rpx;
                    height: 40rpx;
                    border: 1rpx solid #dfdfdf;
                    border-radius: 50%;
                    z-index: 666;
                    background-color: #fff;
                    image{
                        width: 30rpx;
                        height: 30rpx;
                    }
                }
            }
        }
        .functionDoMain{
            display: flex;
            justify-content: space-around;
            align-items: flex-start;
            flex-flow: column nowrap;
            margin: 0 50rpx;
            .functionItem{
                display: flex;
                flex-flow: row nowrap;
                justify-content: flex-start;
                align-items: center;
                margin: 30rpx 0;
                height: 50rpx;
                width: 100%;
                image{
                    width: 50rpx;
                    height: 50rpx;
                }
                span{
                    padding-left: 35rpx;
                    font-size: 30rpx;
                }
            }
        }
        .logOut{
            display: flex;
            flex-flow: row nowrap;
            justify-content: flex-start;
            align-items: center;
            margin: 30rpx 50rpx 150rpx;
            height: 50rpx;
            width: 100%;
            position: absolute;
            bottom: 0;
            left: 0;
            image{
                width: 50rpx;
                height: 50rpx;
            }
            span{
                padding-left: 35rpx;
                font-size: 30rpx;
            }
        }
    }
</style>