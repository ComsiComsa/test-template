<template>
    <div class="item__container">
        {{ label }}
    </div>
</template>

<script>
export default {
    name: 'MyItem',
    props: [ 'label' ]
}
</script>