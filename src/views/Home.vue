<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// import contentful from 'contentful'

import HelloWorld from '@/components/HelloWorld.vue'
const contentful = require('contentful')

// console.log(contentful)
const client = contentful.createClient({
  space: process.env.VUE_APP_CTF_SPACE,
  accessToken: process.env.VUE_APP_CTF_ACCESS_TOKEN
})

// VUE_APP_CTF_ACCESS_TOKEN=zC_xAhi7h7M-uc9W3MKFJW7u_0SWZyCTFOcakpYD1Gg
// VUE_APP_CTF_SPACE=22ro7l3u8i1u
// VUE_APP_CTF_BLOG_POST_TYPE_ID=blogPost

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  async created() {
    const { items } = await this.contentful()
    console.log(items)
  },
  methods: {
    async contentful() {
      return await client.getEntries().then(res => {
        return res
      })
    }
  }
}
</script>
