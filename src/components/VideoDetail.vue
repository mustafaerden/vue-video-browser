<template>
  <div v-if="videoDetail" class="video-detail">
    <div class="embed-responsive embed-responsive-16by9">
      <!-- src yi v-bind:src veya kısaca :src ile yazıyoruz. video linkini uzun uzun yazmak yerine computed function yazıp fonksiyonu :src'function' olarak yazabiliriz -->
      <iframe
        class="embed-responsive-item"
        :src="videoUrl"
        allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
    <div class="details">
      <h4>{{videoDetail.snippet.title}}</h4>
      <p>{{videoDetail.snippet.description}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["videoDetail"],
  computed: {
    videoUrl() {
      // return "https://www.youtube.com/embed/" + this.videoDetail.id.videoId;
      return `https://www.youtube.com/embed/${this.videoDetail.id.videoId}`;
    }
  }
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