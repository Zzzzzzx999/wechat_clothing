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
          <span>Settings</span>
      </div>
      <div class="settingDetail item">
         <span>E-mail</span>
         <div class="setItem" :class="{'active':focus.name}">
            <input type="text" placeholder="ebizmirli@marier.com" placeholder-style="color:black" @focus="focus.name=true" @blur="focus.name=false">
            <image src="../../static/icon/FeatherIconSet/Feather_Controls/edit.png"></image>
         </div>
      </div>
      <div class="passWord item" :class="{'active':focus.passWord}">
         <span>Password</span>
         <div class="setItem">
            <input type="text" placeholder-style="color:black" @focus="focus.passWord=true" @blur="focus.passWord=false">
            <image src="../../static/icon/FeatherIconSet/Feather_Controls/edit.png"></image>
         </div>
      </div>
      <div class="notification item" :class="{'active':focus.notification}">
         <span>Notification</span>
         <div class="setItem" @click="changeNotification=true">
            <input type="text" v-model="finalNotificantion" placeholder="Off" disabled="true" placeholder-style="color:black" @focus="focus.notification=true" @blur="focus.notification=false">
            <image src="../../static/icon/FeatherIconSet/Feather_Chevron/chevron-down.png"></image>
         </div>
      </div>
    </div>
    <!-- 更改消息是否提醒 -->
    <div class="notificationActive changing" v-if="changeNotification">
      <div class="content">
          <div class="title">
              <span>提醒开关</span>
          </div>
          <radio-group @change="radioChange">
            <label class="lan" v-for="(item,index) in notificantion" :key="item.value">
                <div class="lanItem">{{item}}</div>
                <div class="radio" @click="btnCheck(index)">
                    <div :class="{'radio-active':index === notifiIndex}"></div>
                </div>
            </label>
			</radio-group>
			<button @click="done()">DONE</button>
      </div>
    </div>
</div>
  
</template>

<script>
export default {
    name:"setting",
    data() {
        return {
            changeNotification:false,
            notifiIndex:0,
            notificantion:['Off','On'],
            finalNotificantion:'',
            focus:{
                name:false,
                passWord:false,
                notification:false,
            }
        }
    },
    methods: {
        btnCheck(index){
            this.notifiIndex=index
            // this.finalNotificantion=this.notificantion[index]
        },
        done(){
            this.finalNotificantion=this.notificantion[this.notifiIndex]
            this.changeNotification=false
        }
    },
}
</script>

<style lang="less">
    .s{
        height: 100vh;
        position: relative;
    }
    .functionalArea{
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
    .setting{
        margin: 50rpx;
        .title{
            font-size: 42rpx;
            font-weight: 600;
            margin: 30rpx 0;
        }
        .setItem{
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            image{
                width: 50rpx;
                height: 50rpx;
                position: absolute;
                top: 8rpx;
                right: 10rpx;
                transform: translate(-50%,50%);
            }
            span{
                font-size: 30rpx;
            }
            input{
                display: flex;
                border: 3rpx solid #c6cbcc;   
                border-radius: 50rpx;
                width: 100%;
                height: 85rpx;
                margin: 15rpx 0;
                padding-left: 35rpx;
                box-sizing: border-box;
                font-size: 30rpx;
            }
        }
        .item{
            span{
                font-size: 30rpx;
            }
        }
    }
    .notificationActive{
        position: absolute;
        bottom: 0;
        background-color: wheat;
        height: 500rpx;
        width: 100vw;
        z-index: 6;
    }
    .changing{
        // height: 850rpx;
        height: 560rpx;
        width: 100vw;
        background-color: #dfdfdf;
        position: absolute;
        bottom: 0;
        border-top-left-radius: 50rpx;
        border-top-right-radius: 50rpx;
        z-index: 666;
        .content{
            margin: 50rpx;
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
    }
    .active input{
		border: 3rpx solid rgb(177, 45, 45)!important;
	}
</style>