<template>
  <div class="experience">
  	<div class="container">
  	 <span class="tip">WHERE I DID</span>
  	  <h1 class="title">{{title}}</h1>
  	  <span class="border"></span>
  	  <ul class="content">
  	  	<li>
  	  		<div class="content_left tx_right">
  	  		  <span class="s1"></span>
  	  		  <h4>2014 - 2015 </h4>
  	  		</div>
  	  		<div class="content_right tx_left">
  	  		  <h4>公司名1</h4>
  	  		  <p>相关项目详细介绍...</p>
  	  		</div>
  	  		<div class="clearfix"></div>
  	  	</li>
  	  	<li>
  	  		<div class="content_left tx_right">
  	  		  <span class="s2"></span>
  	  		  <h4>2015 - 2016 </h4>
  	  		</div>
  	  		<div class="content_right tx_left">
  	  		  <h4>公司名2</h4>
  	  		  <p>相关项目详细介绍...</p>
  	  		</div>
  	  		<div class="clearfix"></div>
  	  	</li>
  	  	<li>
  	  		<div class="content_left tx_right">
  	  		  <span class="s1"></span>
  	  		  <h4>2016 - 2017 </h4>
  	  		</div>
  	  		<div class="content_right tx_left">
  	  		  <h4>公司名3</h4>
  	  		  <p>相关项目详细介绍...</p>
  	  		</div>
  	  		<div class="clearfix"></div>
  	  	</li>
  	  	<li>
  	  		<div class="content_left tx_right">
  	  		  <span class="s2"></span>
  	  		  <h4>2017 - 2018 </h4>
  	  		</div>
  	  		<div class="content_right tx_left">
  	  		  <h4>公司名4</h4>
  	  		  <p>相关项目详细介绍...</p>
  	  		</div>
  	  		<div class="clearfix"></div>
  	  	</li>
  	  </ul>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'experience',
  data () {
    return {
    	title: '学历与工作'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.experience{
		height: auto;
		width: 100%;
		margin: 0 auto;
		background-color: #fff;
		text-align: center;
		overflow: hidden;
	}
  .container{
		height: auto;
		max-width: 1200px;
		margin: 0 auto;
		padding:4% 5%;
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
		color: #2F2C06;
		font-size: 36px;
		margin: 20px 0;
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

	ul.content{
		padding-top: 20px;
	}
  ul.content li{
		font-size: 20px;
		color:#999;
		position: relative;
		display: flex;
		align-items: flex-start;
		margin-bottom: 40px;
	}
  .content_left{
		flex: 0 0 50%;
		padding: 25px 6% 0 0;
		text-align: right;
		box-sizing: border-box;
	}
  .content_left h4{
		display: inline-block;
		position:relative;
		padding: 10px 40px;
		font-size:20px;
		color: #fff;
		background-color: #1b242f;
		border-radius: 4px;
	}
  /* 绝对定位居中，如果在没有固定高度宽度的盒子里，不要使用百分比定位，使用px，rem，居中用50%+margin负值 */
  .content_left h4:before{
		width: 0;
		height: 0;
		position:absolute;
		top: 50%;
		margin-top: -6px;
		right:-10px;
		content: '';
		border-style: solid;
		border-width: 6px 0 6px 10px;
		border-color: transparent transparent transparent #1b242f;
	}
  .content_right{
		flex: 1;
		padding: 20px 0 10px 6%;
		text-align: left;
		box-sizing: border-box;
		border-left: 1px solid #999;
		position: relative;
	}
  .content_right h4{
		display:inline-block;
		padding: 10px 50px;
		margin-bottom:6px;
		font-size: 20px;
		border: 1px solid #d4d4d4;
		color: #1b242f;
		box-shadow: 0 1px 6px rgba(0, 0, 0, 0.175);
		border-radius: 4px;
	}
  .content_right p{
		line-height: 20px;
		font-size: 14px;
		margin-top: 10px;
	}
	/*小图标*/
  ul.content li span{
		position: absolute;
		top: 30px;
		left: 50%;
		transform: translateX(-50%);
		z-index:10;
		width: 36px;
		height: 36px;
		border-radius: 50%;
		background: url('../common/images/icon.png') no-repeat center;
		background-size: 50%;
	}
  ul.content li .s1{
		background-color: #44c7f4;
	}
  ul.content li .s2{
		background-color: #eb5424;
	}

	/* 响应式设计 - 平板 */
	@media screen and (max-width: 1024px) {
		.container {
			padding: 4% 3%;
		}

		.title {
			font-size: 32px;
		}

		.content_left h4 {
			font-size: 18px;
			padding: 8px 30px;
		}

		.content_right h4 {
			font-size: 18px;
			padding: 8px 40px;
		}

		ul.content li {
			font-size: 18px;
		}
	}

	/* 响应式设计 - 手机端 */
	@media screen and (max-width: 768px) {
		.container {
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

		ul.content li {
			flex-direction: column;
			text-align: center;
			margin-bottom: 30px;
		}

		.content_left {
			flex: none;
			width: 100%;
			padding: 0 0 15px 0;
			text-align: center;
		}

		.content_left h4 {
			font-size: 16px;
			padding: 8px 25px;
		}

		.content_left h4:before {
			display: none;
		}

		.content_right {
			flex: none;
			width: 100%;
			padding: 15px 20px;
			border-left: none;
			border-top: 1px solid #999;
			text-align: center;
		}

		.content_right h4 {
			font-size: 16px;
			padding: 8px 30px;
		}

		.content_right p {
			font-size: 13px;
			line-height: 1.5;
		}

		ul.content li span {
			top: auto;
			bottom: -18px;
			left: 50%;
			transform: translateX(-50%);
		}
	}

	/* 响应式设计 - 小屏手机 */
	@media screen and (max-width: 480px) {
		.container {
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

		ul.content li {
			margin-bottom: 25px;
		}

		.content_left h4 {
			font-size: 14px;
			padding: 6px 20px;
		}

		.content_right {
			padding: 10px 15px;
		}

		.content_right h4 {
			font-size: 14px;
			padding: 6px 20px;
		}

		.content_right p {
			font-size: 12px;
		}

		ul.content li span {
			width: 30px;
			height: 30px;
			bottom: -15px;
		}
	}

	/* 超小屏优化 */
	@media screen and (max-width: 360px) {
		.container {
			padding: 4% 2%;
		}

		.title {
			font-size: 22px;
		}

		.content_right {
			padding: 8px 10px;
		}

		.content_left h4 {
			font-size: 13px;
			padding: 5px 15px;
		}

		.content_right h4 {
			font-size: 13px;
			padding: 5px 15px;
		}
	}
</style>
