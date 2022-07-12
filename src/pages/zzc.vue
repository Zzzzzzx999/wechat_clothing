<template>
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
</template>

<script>
export default {
    name:'zzc',
    data() {
        return {
            // 侧滑栏
            start_clientX:0, //手指触摸开始
            end_clientX:0, //手指触摸结束
            windowWidth:wx.getSystemInfoSync().windowWidth, //获取屏幕宽度
            translate:'',
            username:'Efsan Izmirli',
        }
    },
    props:['showDialog'],
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
        logOut(){
            wx.redirectTo({url:'./index/signIn'})
        },
        btnPath(a){
            wx.redirectTo({url:a})
        }
    },
}
</script>

<style lang="less">
.home{
    transition: all .15s;
}
.home-hide{
    margin-left: 650rpx;
}
.mask{
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, .3);
    position: fixed;
    top: 0;
    left: -100vh;
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