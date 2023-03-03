<template>
    <div
        v-if="selectedLeftItems.length"
        class="show__left"
    >
        <div class="show__list">
            <MyItem
                v-for="item in selectedLeftItems"
                :key="item.id"
                :label="item.name"
            />
        </div>

        <div class="show__label">
            {{ selectedCountLabel }}
        </div>
    </div>

    <MyItem
        v-if="selectedRightItem"
        class="full-height border-large-solid w-200 ml-auto"
        :label="selectedRightItem.name"
    />
</template>

<script>
import { useMainStore } from '../stores/main.js'
import { storeToRefs } from 'pinia'
import MyItem from "./MyItem.vue";

export default {
    name: 'ShowItems',
    components: {MyItem},
    setup () {
        const mainStore = useMainStore()

        const {
            selectedLeftItems,
            selectedRightItem,
            selectedCountLabel
        } = storeToRefs(mainStore)

        return {
            selectedLeftItems,
            selectedRightItem,
            selectedCountLabel
        }
    }
}
</script>