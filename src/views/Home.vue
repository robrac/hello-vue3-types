<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <img alt="Vue logo" :src="girlImg.imgUrl" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src
import { reactive } from 'vue'

interface Image {
  imgUrl: string;
}

@Options({
  components: {
    HelloWorld
  }
})
export default class Home extends Vue {
  girlImg = reactive<Image>({ imgUrl: '' })
  mounted () {
    this.axios.get('https://apiblog.jspang.com/default/getGirl').then(res => {
      this.girlImg = res.data
      console.log(this.girlImg)
    })
  }
}
</script>
