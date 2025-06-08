<template>
  <div class="home">
  	<top>
  		<vue-particles
  		  color="#ffffff"
  		  :particleOpacity="0.7"
  		  linesColor="#ffffff"
  		  :particlesNumber="isMobile ? 30 : 80"
  		  shapeType="circle"
  		  :particleSize="isMobile ? 3 : 5"
  		  :linesWidth="isMobile ? 1 : 2"
  		  :lineLinked="true"
  		  :lineOpacity="0.4"
  		  :linesDistance="isMobile ? 1 : 2"
  		  :moveSpeed="isMobile ? 2 : 3"
  		  :hoverEffect="!isMobile"
  		  hoverMode="grab"
  		  :clickEffect="!isMobile"
  		  clickMode="push"
  		>
  		</vue-particles>
  	</top>
  	<about/>
  	<experience/>
  	<skill/>
  	<project/>
  	<bottom/>
  </div>
</template>

<script>
import top from '@/components/top'
import bottom from '@/components/bottom'
import about from '@/components/about'
import experience from '@/components/experience'
import skill from '@/components/skill'
import project from '@/components/project'
export default {
  name: 'home',
  data () {
    return {
      isMobile: false
    }
  },
  mounted() {
    this.checkMobile();
    window.addEventListener('resize', this.checkMobile);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkMobile);
  },
  methods: {
    checkMobile() {
      this.isMobile = window.innerWidth <= 768;
    }
  },
  components:{
  	top,
  	bottom,
  	about,
  	experience,
  	skill,
  	project
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.home{
		width: 100%;
		height: auto;
		overflow-x: hidden;
	}

	/* 响应式优化 */
	@media screen and (max-width: 768px) {
		.home {
			padding: 0;
		}
	}
</style>

