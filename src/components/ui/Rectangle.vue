<template>
    <div class="rectangle">
        <h2 v-if="title" class="rectangle__title ">{{title}}</h2>
        <slot />
    </div>
</template>

<script>
export default {
    name: 'Rectangle',
    props: {
        title: String
    }
}
</script>

<style scoped lang="scss">
    .rectangle {
        width: 100%;
        background-color: #FFFFFF;
        margin-bottom: 20px;
        border-radius: 24px;
        &__title {
            margin-left: 23px;
            margin-top: 19px;
            padding-bottom: 10px;
            font-weight: bold;
            font-size: 1.25rem;
            display: block;
            border-bottom: 1px solid #EEEEF2;
        }
    }
</style>


