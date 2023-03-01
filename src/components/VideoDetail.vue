<template>
  <div class="col-md-8" v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        :src="videoUrl"
        frameborder="0"
      ></iframe>
    </div>
    <div class="details">
      <h4>
        {{ video.snippet.title }}
      </h4>
      <p>{{ video.snippet.description }}</p>
    </div>
    <iframe
      style="border-radius: 12px"
      src="https://open.spotify.com/embed/artist/3WrFJ7ztbogyGnTHbHJFl2?utm_source=generator"
      width="100%"
      height="380"
      frameBorder="0"
      allowfullscreen=""
      allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
      loading="lazy"
    ></iframe>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
