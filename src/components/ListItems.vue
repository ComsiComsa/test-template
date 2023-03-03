<template>
    <div class="items__container">
        <MyItem
            class="item__container"
            v-for="item in items"
            :key="item.id"
            :label="item.name"
            @click="$emit('handleClick', item)"
        />
    </div>
</template>

<script>
import MyItem from './MyItem.vue';

export default {
    name: 'ListItems',
    components: {
        MyItem
    },
    props: ['items'],
    emits: ['handleClick']
}
</script>

<style scoped>

</style>