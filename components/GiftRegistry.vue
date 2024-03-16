<template>
    <div gift-registry>
        <div class="letter-title">Gift Registry</div>
        <p class="letter-description">Your love, laughter and company on my birthday is the greatest gift of all. However, should you wish to surprise me with a gift, <br>my friends can give you some tips *wink*</p>
        <div class="gifts">
            <div class="gift-item" v-for="(gift, g) in gifts" :key="g" @click="flip(g)" :class="{ 'flipped': flipped === g }">
                <div class="gift-card">
                    <div class="gift-front">
                        <img :src="gift.image">
                    </div>
                    <div class="gift-back">
                        <div class="gift-content">
                            <div class="gift-description">{{ gift.description }}</div>
                            <template v-if="gift.name === 'cash'">
                                <a href="/qr.png" target="_blank" style="height: 50%;"><img :src="gift.qr" class="gift-qr"></a>
                            </template>
                            <template v-else>
                                <a :href="gift.url" class="gift-link" target="_blank">Where to buy</a>
                            </template>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
const attendance = ref(null)
const flipped = ref(null);
const gifts = ref([{
    image: '/friend_001.svg',
    name: 'toys',
    url: 'https://shopee.ph/shop.hoshi?shopCollection=246100916#product_list'
}, {
    image: '/friend_003.svg',
    name: 'hygiene',
    url: 'https://shopee.ph/product/28371224/18953405666?d_id=81a86'
}, {
    image: '/friend_004.svg',
    name: 'wipes',
    url: 'https://shopee.ph/product/554793802/18588213593?d_id=81a86'
}, {
    image: '/friend_005.svg',
    name: 'stroller',
    url: 'https://shop.healthyoptions.com.ph/search?q=Happy%20Baby'
}, {
    image: '/friend_006.svg',
    name: 'bottle cleanser',
    url: 'https://shopee.ph/product/16290154/3705297443?d_id=81a86'
}, {
    image: '/friend_007.svg',
    name: 'nappies',
    url: 'https://s.lazada.com.ph/s.jXvrW'
}, {
    image: '/friend_008.svg',
    name: 'books',
    url: "https://shopee.ph/SOBY-PH-Toddlers-Baby-book-ERIC-CARLE-Board-Book-Set-Children's-Classic-Early-Readers-(11-12pcs)-i.111718901.13024123493"
}, {
    image: '/friend_009.svg',
    name: 'detergent',
    url: 'https://shopee.ph/product/16290154/4405203598?d_id=81a86'
}, {
    image: '/friend_002.svg',
    name: 'cash',
    description: 'GCash is the key -> 09999768395',
    qr: '/qr.png'
}]);

const flip = (f) => {
    if (flipped.value === f) {
        flipped.value = null;
    } else {
        flipped.value = f;
    }

}
</script>
