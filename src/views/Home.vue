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
    {title: '1', time: 'some time', url: 'https://picsum.photos/id/1/400', author:'Joe'},
    {title: '2', time: '24.11.20. 05:34', url: 'https://picsum.photos/id/2/400', author:'Meri'},
    {title: '3', time: '23.11.20. 04:21', url: 'https://picsum.photos/id/3/400', author:'Lee'},
    {title: '4', time: '22.11.20. 08:28', url: 'https://picsum.photos/id/4/400', author:'Bob'},
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
                card => card.title.includes(store.searchTerm) || 
                    card.author.includes(store.searchTerm)
            )
        }
    },
    components: {
        InstagramCard,
    },
};
</script>
