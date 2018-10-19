<template>
  <li
    class="list-group-item media"
    @click="onVideoSelect"
  >
    <img
      class="mr-3"
      :src="thumbnailUrl"
      :alt="video.snippet.title"
    >
    <div class="media-body">
      {{video.snippet.title}}
    </div>
  </li>
</template>

<script>
  export default {
    name: 'VideoListItem',
    props: {
      video: Object
    },
    computed: {
      thumbnailUrl() {
        return this.video.snippet.thumbnails.default.url
      }
    },
    methods: {
      onVideoSelect() {
        this.$emit('videoSelect', this.video)
      }
    }
  }
</script>

<style scoped>
  li {
    cursor: pointer;
    display: grid;
    grid-gap: 1rem;
    grid-template-columns: 120px auto;
    transition: background-color 0.5s ease;
  }

  li:hover {
    background-color: #eee;
  }
</style>
