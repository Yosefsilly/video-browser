<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="thumbnailURL" />
    <div class="media-body">
    <h5 class="mt-0 mb-1">
    {{ video.snippet.title }}
    </h5>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video",],
  computed: {
    thumbnailURL() {
        return this.video.snippet.thumbnails.default.url
    }
  },
  methods: {
    onVideoSelect() {
        this.$emit('videoSelect', this.video)
    }
  }
};
</script>

<style scoped>
li {
    display: flex;
    cursor: pointer;
}

li:hover {
    background-color: #eee;
}
</style>
