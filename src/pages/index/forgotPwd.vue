<template>
	<div class="content">
		<image class="bg" mode="scaleToFill" src="../../static/start(2).png"></image>
		<image class="bg2" src="../../static/start(1).png"></image>
		<div class="signIn">
			<span class="title">Forgot Password ?</span>
			<div class="text">
				<span>Please enter your email address.You will receive a link to create a new password via email.</span> 
			</div>
			<div class="login">
				<div class="userInfo" :class="emailFocus?'active':''">
					<span>E-mail</span><br> 
					<input type="text" placeholder="ebizmirli@marier.com" @focus="emailFocus=true" @blur="emailFocus=false" maxlength="16" confirm-type="done" placeholder-style="color:black">
				</div>
				<div class="sendButton">
					<button @click="btnPath('./signIn')">SEND NEW PASSWORD</button>
				</div>
				<div class="loginSocial">
					<div class="notAccount">
						<span>Don' t have an account?</span>
						<span id="bolder" @click="signUp">Sign Up</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name:'forgotPwd',
		data() {
			return {
				emailFocus:false,
				passwordFocus:false,
			}
		},
		onLoad() {
			
		},
		methods: {
			handleFocus(){
				this.focus=true
				console.log(this.focus,'获取到了焦点');
			},
			handleBlur(){
				this.focus=false
				console.log(this.focus,'失去了焦点');
			},
			signUp(){
				uni.navigateTo({url:'./signUp'})
			},
			btnPath(a){
				wx.redirectTo({url:a})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: center;
		height: 100vh;
		width: 100vw;
		position: relative;
		margin: 0;
		padding: 0;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.title{
		font-size: 40rpx;
		font-weight: 600;
	}

	.bg{
		width: 800rpx;
		height: 900rpx;
		position: absolute;
		top: 0;
		left: 0;
		background-size:100% 100%;
		filter: brightness(0.65);
		z-index: -2;
	}

	.bg2{
		width: 200rpx;
		height: 200rpx;
		position: absolute;
		top: 10%;
		left: 50%;
		transform: translate(-50%,-20%);
		background-size:100% 100%;
		z-index: -1;
	}

	.signIn{
		width: 100%;
		height: 50vh;
		position: absolute;
		bottom: 0;
		background-color: whitesmoke;
		border-radius: 5%;
		display: flex;
		justify-content: space-around;
		align-items: center;
		flex-flow: column nowrap;
		padding-bottom: 50rpx;
		box-sizing: border-box;
	}

	.signIn .title{
		margin: 40rpx 0rpx 20rpx;
	}

	.signIn .text{
		padding: 0px 65rpx;
    	font-size: 28rpx;
	}

	.content .signIn .login{
		font-size: 35rpx;
		color: rgb(48, 46, 46);
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
	}
/* 
	.content .signIn .login .userInfo{
		padding-top: 20rpx;
	} */

	.content .signIn .login .userInfo input{
		display: flex;
		border: 3rpx solid #c6cbcc;   
  		border-radius: 50rpx;
		width: 630rpx;
		height: 85rpx;
		margin: 15rpx 0;
		padding-left: 35rpx;
		box-sizing: border-box;
		font-size: 30rpx;
	}

	.active input{
		border: 3rpx solid rgb(177, 45, 45)!important;
	}

	.content .signIn .login .userInfo .password{
		display: flex;
		justify-content: center;
		align-items: center;
		position: relative;
	}

	.content .signIn .login .userInfo .password image{
		position: absolute;
		right: 25rpx;
		width: 60rpx;
		height: 60rpx;
	}

	.content .signIn .login .forgotPassword{
		display: block;
		text-align: right;
		margin-top: 20rpx;
		color: black;
		font-size: 35rpx;
	}

	.content .signIn .login .forgotPassword span{
		text-align: center;
		font-weight: 600;
	}

	.content .signIn .login .sendButton{
		margin-top: 20rpx;
	}

	.content .signIn .login .sendButton button{
		border-radius: 50rpx;
		color: white;
		background-color: #21bff0;
		font-size: 35rpx;
		border-radius: 50rpx;
		margin: 0;
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		cursor: pointer;
	}
	.content .signIn .login .loginSocial{
		display: flex;
		flex-flow: column nowrap;
		justify-content: center;
		align-items: center;
		margin-top: 20rpx;
	}
	.content .signIn .login .loginSocial span{
		margin: 15rpx 0;
	}
	.content .signIn .login .loginSocial #bolder{
		color: rgb(48, 46, 46);
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		font-weight: 600;
	}
	.content .signIn .login .loginSocial .notAccount{
		margin-top: 20rpx;
	}
	.content .signIn .login .loginSocial .notAccount span:last-child{
		margin-left: 10rpx;
	}
</style>
