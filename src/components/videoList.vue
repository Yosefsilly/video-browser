<template>
  <div class="col-md-4">
    <ul class="list-group">
      <video-list-item
        v-for="video in videos"
        v-bind:key="video.etag"
        v-bind:video="video"
        @videoSelect="onVideoSelect"
      >
      </video-list-item>
    </ul>
  </div>
</template>

<script>
import VideoListItem from "./videoListItem.vue";
export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: ["videos"],
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style></style>
