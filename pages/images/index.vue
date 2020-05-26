<template>
  <div>
    <h1>Background images for im.marlsantos.com</h1>    
    <div class="content">
      <div
        v-for="(thumb, thumbIndex) in images"        
        :key="thumbIndex"
        @click="index = thumbIndex"
        class="row"
      >
        <img :src="thumb.url" width="100" height="100">
      </div>    
      <LightGallery
        :images="images"
        :index="index"
        :disable-scroll="true"
        @close="index = null"
      />
    </div>
  </div>
</template>

<script>
  import { LightGallery } from 'vue-light-gallery';

  export default {
    components: {
      LightGallery,
    },
    name: 'backgroundImages',
    asyncData() {
      return new Promise((resolve) => {
        resolve({images: [], index: null })
      });
    },
    mounted() {
      this.importAll(require.context('/sdcard/Download/Wallpaper/Compressed', false, /\.jpg$/));
    },
    methods: {
      importAll(r) {
        r.keys().forEach(key => (this.images.push({ title: key.replace('./',''), url: r(key), index: key })));
      },
    },
  };
</script>

<style scoped>
  .content {
    display: flex;
    width: 90%;
    margin: 20px;
    flex-wrap: wrap;
  }
  .column {
    flex-direction: column;
  }
  .row {
    flex-direction: row;
    margin: 5px !important;
  }
  h1 {
    font-size: 18px; 
    text-align: center;
    margin: 20px;
  }
</style>