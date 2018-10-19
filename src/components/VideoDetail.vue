<template>
  <div
    class="video"
    v-if="video"
  >
    <div class="video-embed">
      <div class="embed-responsive embed-responsive-16by9">
        <iframe
          class="embed-responsive-item"
          :src="videoUrl"
          frameborder="0"
          allow="autoplay; encrypted-media"
          allowfullscreen
        >
      </iframe>
      </div>
    </div>
    <div class="video-details">
      <h4>{{video.snippet.title}}</h4>
      <p>{{video.snippet.description}}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'VideoDetail',
    props: {
      video: Object,
    },
    computed: {
      videoUrl() {
        const { videoId } = this.video.id
        return `https://www.youtube.com/embed/${videoId}`
      },
    },
  }
</script>

<style scoped>
  .video {
    margin-bottom: 1rem;
  }
  .video-details {
    background-color: #eee;
    border: 1px solid rgba(0, 0, 0, .125);
    border-radius: 4px;
    margin-top: 1rem;
    padding: 1rem;
  }
</style>
