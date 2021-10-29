<template>
    <div>
        <input class="custom-input" type="text" :placeholder="placeholder" v-model="text">    
    </div>
</template>

<script>
export default{
    name: 'CustomInput',
    props: {
        placeholder: String
    },
    data () {
        return {
            text: ''
        }
    }  
}
</script>

<style scoped lang="scss">
    .custom-input {
        width: 100%;
        border: 1px solid #CCD4E0;
        outline: none;
        padding-left: 5px;
        height: 42px;
        margin-bottom: 10px;
    }
</style>