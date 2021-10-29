<template>
    <Rectangle title='Budget'>
        <p class="header"><span class="header--bold">20.00 RON</span>Total budget</p>
        <p class="subheader">146-432 Estimated reach</p>
        <Range title="Influencers" :to="500" />
        <Range title="Posts" :to="100" />
        <button class="btn budget-btn">Continue</button>
    </Rectangle>
</template>

<script>
import Rectangle  from '../ui/Rectangle'
import Range from '../ui/Range'

export default {
    name: 'Budget',
    components: {
        Rectangle, Range
    }
}
</script>

<style scoped lang="scss">
    .header {
        color: #7A828F;
        font-size: 1.56rem;
        font-weight: bold;
        white-space: nowrap;
        margin-top: 34px;
        margin-left: 16px;
        &--bold {
            font-size: 2.18rem;
            font-weight: 800;
        }
    }
    .subheader {
        font-size: 1,5rem;
        margin-left: 16px;
        color: #9798B2;
    }
    .budget-btn {
        width: calc(100% - 46px);
        height: 52px;
        color: #ffffff;
        background: #9637F1;
        font-size: 1.25rem;
        margin-left: 23px;
        margin-right: 23px;
        margin-bottom: 20px;
        border-radius: 16px;
    }
</style>