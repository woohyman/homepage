<template>
  <div class="progress-box">
    <p>{{skill.type}}</p>
    <div class="container">
    	<div class="progress-bar progress-bar-striped active" :style="{width:skill.percent}"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'progress-bar',
  props: {
    skill: {
      type: Object
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.progress-box {
	margin-bottom: 20px;
}

.progress-box p{
	font-size: 24px;
	color:#2F2C06;
	text-align: left;
	margin-bottom: 8px;
	font-weight: 500;
}

.container{
	height: 12px;
	margin: 16px 0;
	background-color: #e8edf2;
	overflow: hidden;
	border-radius: 6px;
	box-shadow: 0 2px 8px rgba(0,0,0,0.1);
	position: relative;
}

.progress-bar {
	height: 100%;
	background-color: #03a9f4;
	transition: width 1.5s ease-in-out;
	border-radius: 6px;
}

.progress-bar.active {
	animation: progress-bar-stripes 2s linear infinite;
}

.progress-bar-striped {
	background-image: linear-gradient(45deg, rgba(255, 255, 255, .15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .15) 50%, rgba(255, 255, 255, .15) 75%, transparent 75%, transparent);
	background-size: 40px 40px;
}

@keyframes progress-bar-stripes {
  from {background-position: 40px 0;}
  to {background-position: 0 0;}
}

/* 响应式设计 - 平板 */
@media screen and (max-width: 1024px) {
	.progress-box p {
		font-size: 22px;
	}

	.container {
		height: 10px;
		margin: 14px 0;
	}
}

/* 响应式设计 - 手机端 */
@media screen and (max-width: 768px) {
	.progress-box {
		margin-bottom: 15px;
	}

	.progress-box p {
		font-size: 18px;
		text-align: center;
		margin-bottom: 6px;
	}

	.container {
		height: 8px;
		margin: 12px 0;
		border-radius: 4px;
	}

	.progress-bar {
		border-radius: 4px;
	}

	.progress-bar-striped {
		background-size: 30px 30px;
	}
}

/* 响应式设计 - 小屏手机 */
@media screen and (max-width: 480px) {
	.progress-box {
		margin-bottom: 12px;
	}

	.progress-box p {
		font-size: 16px;
		margin-bottom: 5px;
	}

	.container {
		height: 6px;
		margin: 10px 0;
	}

	.progress-bar-striped {
		background-size: 20px 20px;
	}
}

/* 超小屏优化 */
@media screen and (max-width: 360px) {
	.progress-box p {
		font-size: 14px;
	}

	.container {
		margin: 8px 0;
	}
}
</style>

