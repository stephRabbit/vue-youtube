<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo"></VideoDetail>
    <VideoList
      :videos="videos"
      @videoSelect="onVideoSelect"
    >
    </VideoList>
  </div>
</template>


<script>
  import axios from 'axios'
  import { YT_API_KEY } from '../config'

  import SearchBar from './components/SearchBar'
  import VideoDetail from './components/VideoDetail'
  import VideoList from './components/VideoList'

  export default {
    name: 'App',
    data() {
      return {
        videos: [],
        selectedVideo: null,
      }
    },
    components: {
      SearchBar,
      VideoList,
      VideoDetail,
    },
    methods: {
      async onTermChange(searchTerm) {
        const response = await axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: YT_API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })

        const { data } = response
        this.videos = data.items
      },
      onVideoSelect(video) {
        this.selectedVideo = video
      },
    },
  }
</script>