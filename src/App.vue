<template>
  <div style="height: 100%; width: 100%" id="app">
    <div style="width: 50%;display: inline-block;height: 100%;">
      <textarea
        @input="changeHandler"
        style="width: 100%; height: 200px;"
        v-model="value"
      ></textarea>
      <pdf-make
        ref="pdfMake"
        style="width: 100%"
        :show="true"
        :info="{ title: '测试' }"
        @change="e => (src = e)"
      >
        hello world
        <div style="font-size: 50px">
          <a
            style="margin-top: 20px; margin: 10px;"
            href="https://www.baidu.com"
          >
            {{ value }}
          </a>
        </div>
        <span style="font-weight: 600;text-align: center;">span</span>
        <img
          width="100px"
          src="https://is4-ssl.mzstatic.com/image/thumb/Purple128/v4/0b/18/23/0b18235d-9a98-e913-12db-2705bb5278d4/AppIcon-0-1x_U007emarketing-0-85-220-10.png/246x0w.jpg"
        />
      </pdf-make>
    </div>
    <iframe
      v-if="src"
      :src="src"
      style="width: 50%;display: inline-block;height: 100%;"
      frameborder="0"
    ></iframe>
  </div>
</template>

<script>
import PdfMake from './components/PdfMake'
import ttf from 'url-loader!./assets/微软雅黑.ttf'
console.log(ttf)
export default {
  name: 'app',
  components: {
    PdfMake,
  },
  data() {
    return {
      src: '',
      value: '',
    }
  },
  methods: {
    changeHandler() {
      this.$refs.pdfMake.createPdf()
    },
  },
}
</script>
<style>
html,
body {
  margin: 0px auto;
  padding: 0px;
  height: 100%;
}
#app {
  margin-bottom: -16px;
  display: flex;
}
</style>
