<template>
    <div class="row">
        <div class="col-2"></div>
        <div class="col-8">
            <instagram-card v-for="card in filteredCards" :key="card" :info="card" />
        </div>
        <div class="col-2"></div>
    </div>
</template>
<script>
// @ is an alias to /src
import InstagramCard from '@/components/InstagramCard.vue';
import store from '@/store.js';

let cards = [
    {title: '1', time: 'some time', url: 'https://picsum.photos/id/1/400'},
    {title: '2', time: 'some time', url: 'https://picsum.photos/id/2/400'},
    {title: '3', time: 'some time', url: 'https://picsum.photos/id/3/400'},
    {title: '4', time: 'some more time', url: 'https://picsum.photos/id/4/400'},
]

export default {
    name: 'home',
    data: function() {
        return {
            cards: cards,
        };
    },
    computed: {
        filteredCards() {
            return this.cards.filter( 
                card => card.title.includes(store.searchTerm)
            )
        }
    },
    components: {
        InstagramCard,
    },
};
</script>
