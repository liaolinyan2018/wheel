<template>
    <svg class="g-icon">
        <use :xlink:href="`#i-${name}`"></use>
    </svg>
</template>

<script>
    export default {
        name: "g-icon",
        props: ['name']
    }
</script>

<style scoped>

</style>