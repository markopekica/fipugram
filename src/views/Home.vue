<template>
    <div class="row">
        <div class="col-8">
            <instagram-card />
            <instagram-card />
        </div>
        <div class="col-4">
            Sidebar
        </div>
    </div>
</template>
<script>
// @ is an alias to /src
import InstagramCard from '@/components/InstagramCard.vue';

export default {
    name: 'home',
    components: {
        InstagramCard,
    },
};
</script>
