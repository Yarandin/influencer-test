<template>
    <div class="range-container">
        <span class="range-container__title">{{title}}</span>
        <span v-if="from" class="range-container__number">{{from}}-{{to}}</span>
        <span v-else class="range-container__number">{{to}}+</span>
        <Slider
            v-model="value"
            class="range-container__range"
            showTooltip="focus"
            :min="from"
            :max="to"
        />
    </div>
</template>

<script>
import Slider from '@vueform/slider/dist/slider.vue2.js'
export default {
    name: 'Range',
    props: {
        title: String,
        from: Number, 
        to: {
            type: [Number, Array],
            default: 20
        }
    },
    components: { Slider },
    data: () => ({
        value: 20
    }),
    mounted () {
        this.value = this.from ? [this.from, this.to] : this.from
    }
}
</script>

<style src="@vueform/slider/themes/default.css"></style>
<style scoped lang="scss">
    .range-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        width: calc(100% - 46px);
        margin-right: 23px;
        margin-left: 23px;
        margin: auto;
        &__title {
            font-size: 1rem;
        }
        &__number {
            font-size: 0.8rem;
            width: 63px;
            background: #F7EFFE;
            border-radius: 8px;
            display: flex;
            justify-content: center;
            color: #966BF5;
        }
        &__range {
            margin-top: 27px;
            width: 100%;
            --slider-height: 2px;
            --slider-connect-bg: #9637F1;
            --slider-tooltip-bg: #9637F1;
            --slider-handle-border: 2px solid #9637F1;
            --slider-handle-ring-width: 2px;
            --slider-handle-ring-color: #9637F1;
            --slider-handle-width: 24px;
            --slider-handle-height: 24px;
            --slider-handle-shadow: none;
            margin-bottom: 35px;
        }
    }
    
</style>