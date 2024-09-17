<template>
  <div class="video-container">
    <iframe
      :src="embedUrl"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </div>
</template>

<script>
export default {
  name: "Youtube",
  props: {
    videoUrl: {
      type: String,
      required: true
    }
  },
  computed: {
    embedUrl() {
      const videoId = this.getVideoId(this.videoUrl);
      console.log(this.videoUrl)
      return `https://www.youtube.com/embed/${videoId}`;
    }
  },
  methods: {
    getVideoId(url) {
      const regExp = /^.*(youtu\.be\/|v\/|\/u\/\w\/|embed\/|watch\?v=|\&v=)([^#\&\?]*).*/;
      const match = url.match(regExp);
      return match && match[2].length === 11 ? match[2] : null;
    }
  }
};
</script>

<style scoped>
.video-container {
  position: relative;
  padding-bottom: 56.25%; /* 16/9 ratio */
  height: 0;
  overflow: hidden;
  margin-bottom: 50px;
}
.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
