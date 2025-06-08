<template>
  <div class="about">
  	<div class="container">
  	  <span class="tip">WHO AM I</span>
  	  <h1 class="title">{{title}}</h1>
  	  <span class="border one"></span>
  	  <div class="a_info">
  	  	<swiper :options="swiperOption" ref="mySwiper">
  	      <!-- slides -->
  	      <swiper-slide>
  	        <p>您在找前端工程师？？</p>
  	      </swiper-slide>
  	      <swiper-slide>
  	        <p>您真的来对了！！</p>
  	      </swiper-slide>
  	      <swiper-slide>
  	        <p>我就是一名热爱前端开发，为前端痴狂的coder。</p>
  	      </swiper-slide>
  	      <swiper-slide>
  	        <p>I Am The One!!</p>
  	      </swiper-slide>
  	      <div class="swiper-pagination" slot="pagination"></div>
	        <div class="swiper-button-prev" slot="button-prev"></div>
	        <div class="swiper-button-next" slot="button-next"></div>
  	    </swiper>
  	  </div>
  	</div>
  </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'about',
  data () {
    return {
      title: '自我简述',
      swiperOption: {
        spaceBetween: 30,
        centeredSlides: true,
        autoplay: {
          delay: 2500,
          disableOnInteraction: false
        },
        pagination: {
          el: '.swiper-pagination',
          clickable: true
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      }
    }
  },
  components: {
    swiper,
    swiperSlide
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.about{
		height: auto;
		width: 100%;
		margin: 0 auto;
		background-color: #f5f5f5;
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
  .a_info{
		font-size: 20px;
		margin: 0 auto;
	}
  .swiper-container{
		width: 100%;
		height: 300px;
		line-height: 300px;
		overflow: hidden;
		text-align: center;
	}
  .swiper-pagination{
		top:46%;
	}

	/* 响应式设计 - 平板 */
	@media screen and (max-width: 1024px) {
		.container {
			padding: 4% 3%;
		}

		.title {
			font-size: 32px;
		}

		.a_info {
			font-size: 18px;
		}

		.swiper-container {
			height: 280px;
			line-height: 280px;
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

		.a_info {
			font-size: 16px;
		}

		.swiper-container {
			height: 200px;
			line-height: 200px;
		}

		.swiper-pagination {
			top: 40%;
		}

		/* 隐藏导航按钮在手机端 */
		.swiper-button-prev,
		.swiper-button-next {
			display: none;
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

		.a_info {
			font-size: 14px;
		}

		.swiper-container {
			height: 150px;
			line-height: 150px;
		}

		.swiper-container p {
			padding: 0 10px;
			line-height: 1.4;
			display: flex;
			align-items: center;
			justify-content: center;
			height: 100%;
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

		.a_info {
			font-size: 13px;
		}

		.swiper-container {
			height: 120px;
			line-height: 120px;
		}
	}
</style>
