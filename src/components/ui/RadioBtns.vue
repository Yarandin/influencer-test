<template>
    <div class="tumbler">
        <div v-for="(btn, index) in btns" :key="btn">
            <input  type="radio" :id="btn" :value="btn" name="radio" class="tumbler__radio-btn" v-model="picked" />
            <label  class="tumbler__btn" :class="[`tumbler__btn-${shape}`, {'tumbler__btn--active': picked == btn, [`tumbler__btn-${color}`]: color} ]" :for="btn">
                <div v-if="svg" v-html="svg[index]"></div>
                {{btn}}
            </label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RadioBtns',
    props: {
        btns: Array,
        shape: String,
        svg: Array,
        color: String
    },
    data() {
        return {
            picked: this.btns[1]
        }
    }
}
</script>

<style scoped lang="scss">
    .tumbler {
        margin-bottom: 10px;
        display: flex;
        justify-content: space-between;
        &__radio-btn {
            opacity: 0;
            position: fixed;
            max-width: 106px;
            width: calc(33% - 10px);
        }
        &__btn-white {
            background: #fff;
        }
        &__btn-light-purple {
            background: #F7EFFE;
        }
        &__btn-square {
            width: 106px;
            height: 35px;
            border-radius: 5px;
        }
        &__btn-ellips {
            width: 64px;
            height: 24px;
            border-radius: 12px;
        }
        &__btn {
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 0.75rem;
            color: #9637F1;
            border: none;
            &--active {
                color: #fff;
                background: #9637F1;
                &::v-deep path {
                    fill: #fff;
                }
                &::v-deep circle {
                    fill: #fff;
                }
            }
        }
    }
    @media (min-width: 768px) { 
        .tumbler {
            justify-content: start;
            &__btn {
                margin-right: 10px;
            }
        }
    }
</style>
