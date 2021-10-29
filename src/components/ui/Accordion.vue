<template>
    <div class='accordion-container' :class="{ 'accordion-container--active': show }"> 
        <div class="accordion-container__title title-container">
            <span class="title-container__title">{{title}}</span>
            <button v-on:click="show = !show" :class="[show ? 'title-container__btn--active' : '', 'title-container__btn', 'btn'] ">                         
                <svg xmlns="http://www.w3.org/2000/svg" width="7.765" height="13.441" viewBox="0 0 7.765 13.441">
                    <path id="Контур_208" data-name="Контур 208" d="M4871.166,592.811l5.351,5.225-5.351,5.388" transform="translate(-4869.752 -591.396)" fill="none" stroke="#9637f1" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"/>
                </svg>
            </button>
        </div>
        <p class="accordion-container__subtitle">{{subtitle}}</p>
        <transition name="fade">
            <slot v-if="show"></slot>
        </transition>
    </div>
</template>

<script>
export default {
    name: 'Accordion',
    props: {
        title: String,
        subtitle: String
    },
    data: () => ({
        show: false,
    })
}
</script>

<style scoped lang="scss">
    .accordion-container{
        margin-top: 10px;
        padding-left: 23px;
        padding-right: 23px;
        padding-bottom: 10px;
        margin: 5px;
        &--active {
            transition:  .5s;
            background: #F8F8F9;
            border-radius: 24px; 
        }
        &__subtitle {
            font-family: 'Montserrat', sans-serif;
            font-size: 0.87rem;
            color: #8998AC;
        }
    }
    .title-container {
        display: flex;
        justify-content: space-between;
        padding-top: 10px;
        &__title {
            font-size: 1rem;
        }
        &__btn {
            
            &--active {
                transform: rotate(90deg);
            }
        }
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to  {
        opacity: 0;
    }

</style>