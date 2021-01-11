<template>
  <div class="card text-center">
    <div class="card-header">
      {{ info.description }}  <!-- i zašto tu mora biti description a ne desc??? možda jer je 03:10 -->
    </div>
    <div class="card-body p-0">
      <img class="card-img-top" :src="info.url" alt="slika" />
    </div>
    <div class="card-footer text-muted">
      <!-- {{ info.id }} -->
      {{ postedFromNow }}
    </div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  props: ["info"],
  name: "InstagramCard",
  computed: {
    postedFromNow() {
      return moment(this.info.time).fromNow()
    }
  }
};
</script>

<style lang="scss">
.card {
  margin-bottom: 20px;
}
</style>
