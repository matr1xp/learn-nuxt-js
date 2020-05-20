<template lang="pug">
  .row
    .col(v-for="client in images")
      img(:src="client.pathLong", :width=100, :height=100)
</template>

<script>
export default {
  name: 'backgroundImages',
  data() {
    return {
      images: [],
    };
  },

  mounted() {
    this.importAll(require.context('/sdcard/LitPhoto', true, /\.jpg$/));
  },

  methods: {
    importAll(r) {
      r.keys().forEach(key => (this.images.push({ pathLong: r(key), pathShort: key })));
    },
  },
};
</script>