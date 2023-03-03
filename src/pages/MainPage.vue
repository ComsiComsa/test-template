<template>
    <div class="main">
        <div class="main__header">
            <ShowUserItems />
        </div>

        <div class="main__bottom">
            <ListItems
                :items="leftItems"
                @handle-click="leftItemClicked"
            />
            <ListItems
                :items="rightItems"
                @handle-click="rightItemClicked"
            />
        </div>
    </div>
</template>

<script>
import { useMainStore } from '../stores/main.js'
import { storeToRefs } from 'pinia'
import ListItems from '../components/ListItems.vue'
import ShowUserItems from '../components/ShowUserItems.vue'

export default {
    name: 'MainPage',
    components: {
        ShowUserItems,
        ListItems
    },
    setup () {
        const mainStore = useMainStore()

        const {
            leftItems,
            rightItems
        } = storeToRefs(mainStore)

        const leftItemClicked = (item) => {
            mainStore.selectLeftItems(item)
        }

        const rightItemClicked = (item) => {
            mainStore.selectRightItems(item)
        }

        return {
            leftItems,
            rightItems,
            leftItemClicked,
            rightItemClicked
        }
    }
}
</script>