<script>
import MediaItem from './MediaItem.vue'

export default {
    components: {
        MediaItem
    },
    props: {
        items: {
            type: Array,
            required: true,
            default:() => []
        }
    }
};

</script>
<template>
    <div v-for="item in items" :key="item.id">
        {{ console.log(item) }}
        <MediaItem :item="item" />
    </div>
</template>
<style></style>