<template>
  <div class="bottom">
  	<div class="container">
  	<span class="tip">HOW TO FIND</span>
  	  <h1 class="title">{{title}}</h1>
  	  <span class="border"></span>
  	  <div class="content">
  	    <img src="../common/images/code.jpg" alt="">
<!--  	    <dl>-->
<!--  	      <dt>Contact By Email</dt>-->
<!--  	      <dd>Mail1: <a href="mailto:info@example.com">info@example1.com</a></dd>-->
<!--  	      <dd>Mail2: <a href="mailto:info@example.com">info@example2.com</a></dd>-->
<!--  	    </dl>-->
  	  </div>
  	  <p v-text="desc"></p>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'bottom',
  data () {
    return {
    	title: '联系我',
    	desc: '© 2018 Preface . All rights reserved | Design by cisco lai.'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.bottom{
		height: auto;
		width: 100%;
		margin: 0 auto;
		background-color: #333333;
		background: url('../common/images/contact.jpg') no-repeat center top;
		background-size: cover;
		padding: 4% 5%;
		position: relative;
		overflow: hidden;
	}

	.bottom::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background: rgba(0, 0, 0, 0.4);
		z-index: 1;
	}

	.container{
		max-width: 1200px;
		margin: 0 auto;
		text-align: center;
		position: relative;
		z-index: 2;
	}

	.tip{
		display:inline-block;
		position:relative;
		padding:6px 20px;
		margin:0 auto 10px;
		font-size: 20px;
		background:#03a9f4;
		color: #fff;
		border-radius: 4px;
	}

	.tip:after{
		position:absolute;
		width: 0;
		height: 0;
		left:42%;
		bottom:-10px;
		content: '';
		border-style: solid;
		border-width: 10px 10px 0 10px;
		border-color: #03a9f4 transparent;
	}

	.title{
		padding: 6px 0 10px;
		font-family: 'Overlock', cursive;
		color: #fff;
		font-size: 36px;
		margin: 20px 0;
		text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
	}

	.border{
		display:block;
		width: 20%;
		height: 1px;
		position:relative;
		margin:0 auto 30px;
		background: #8C8989;
	}

	.border:after{
		position: absolute;
		top: 0;
		left: 30%;
		content: " ";
		width: 40%;
		height: 5px;
		margin-top:-2px;
		background: #03a9f4;
	}

	.content{
		width:45%;
		margin:0 auto;
		background: rgba(245, 245, 245, 0.95);
		border-radius: 15px;
		box-shadow: 0 8px 32px rgba(0,0,0,0.3);
		backdrop-filter: blur(10px);
		padding: 20px;
	}

	.content img{
		width: 40%;
		height: auto;
		margin: 30px 0;
		border-radius: 10px;
		box-shadow: 0 4px 15px rgba(0,0,0,0.2);
	}

	.content dl{
		border-top: 1px solid rgb(214, 212, 212);
		position: relative;
		padding-bottom: 20px;
	}

	.content dl:after{
		position: absolute;
		top: 8%;
		left: 48%;
		content: "";
		width: 16px;
		height: 16px;
		background: url('../common/images/email.png') no-repeat;
		background-size: 100% auto;
	}

	.content dt{
		font-size: 16px;
		margin: 30px 0 10px;
	}

	.content dd{
		font-size: 18px;
		color: #999;
		margin-top: 10px;
	}

	.content dd a{
		font-size: 16px;
		color: #00a78e;
	}

	.bottom p{
		font-size: 14px;
		color: #fff;
		margin-top: 6%;
		text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
	}

	/* 响应式设计 - 平板 */
	@media screen and (max-width: 1024px) {
		.container {
			padding: 0 3%;
		}

		.title {
			font-size: 32px;
		}

		.content {
			width: 60%;
		}

		.content img {
			width: 50%;
		}
	}

	/* 响应式设计 - 手机端 */
	@media screen and (max-width: 768px) {
		.bottom {
			padding: 6% 4%;
		}

		.tip {
			font-size: 16px;
			padding: 5px 15px;
		}

		.tip:after {
			left: 45%;
			border-width: 8px 8px 0 8px;
		}

		.title {
			font-size: 28px;
			padding: 4px 0 8px;
		}

		.border {
			width: 30%;
			margin: 0 auto 25px;
		}

		.content {
			width: 85%;
			padding: 15px;
			border-radius: 12px;
		}

		.content img {
			width: 60%;
			margin: 20px 0;
		}

		.content dt {
			font-size: 14px;
			margin: 20px 0 8px;
		}

		.content dd {
			font-size: 16px;
		}

		.content dd a {
			font-size: 14px;
		}

		.bottom p {
			font-size: 12px;
			margin-top: 8%;
			padding: 0 10px;
		}
	}

	/* 响应式设计 - 小屏手机 */
	@media screen and (max-width: 480px) {
		.bottom {
			padding: 5% 3%;
		}

		.tip {
			font-size: 14px;
			padding: 4px 12px;
		}

		.title {
			font-size: 24px;
		}

		.border {
			width: 40%;
		}

		.content {
			width: 95%;
			padding: 12px;
		}

		.content img {
			width: 70%;
			margin: 15px 0;
		}

		.content dt {
			font-size: 13px;
			margin: 15px 0 6px;
		}

		.content dd {
			font-size: 14px;
		}

		.content dd a {
			font-size: 13px;
		}

		.bottom p {
			font-size: 11px;
			line-height: 1.4;
		}
	}

	/* 超小屏优化 */
	@media screen and (max-width: 360px) {
		.bottom {
			padding: 4% 2%;
		}

		.title {
			font-size: 22px;
		}

		.content {
			width: 98%;
			padding: 10px;
		}

		.content img {
			width: 80%;
		}

		.bottom p {
			font-size: 10px;
		}
	}
</style>
