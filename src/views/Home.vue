<template>
  <div class="row">
    <div class="col-3"></div>
    <div class="col-6">
      <instagram-card />
      <instagram-card />
      <instagram-card />
      <instagram-card />
    </div>
    <div class="col-3"></div>
  </div>
</template>

<script>
import InstagramCard from "@/components/InstagramCard.vue";

export default {
  name: "home",
  components: {
    InstagramCard,
  },
};
</script>
