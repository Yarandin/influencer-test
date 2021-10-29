<template>
    <div class="wrapper-container">
        <div class="tab-btns">
            <RadioBtns :btns="tabs" :svg="tabIcon" shape="square" color="white"/>
        </div>
        <div class="grid">
            <Target class="grid-item"/>
            <Budget class="grid-item"/>
            <Audience class="grid-item"/>
        </div>
    </div>
</template>

<script>
import RadioBtns from '../ui/RadioBtns'
import Target from '../Target/Target'
import Budget from '../Budget/Budget'
import Audience from '../Audience/Audience'

const icon1 = `<svg xmlns="http://www.w3.org/2000/svg" width="20.738" height="11.668" viewBox="0 0 20.738 11.668">
                    <g id="Сгруппировать_3" data-name="Сгруппировать 3" transform="translate(-2.6 -23.3)">
                        <path id="Контур_213" data-name="Контур 213" d="M70.366,46.3a3.38,3.38,0,0,1-2.207.808,3.467,3.467,0,0,1-2.185-.787,4.438,4.438,0,0,0-.874,1.027,6.848,6.848,0,0,1,1.792,4.042c.393.022.83.044,1.289.044a12.509,12.509,0,0,0,3.671-.5.473.473,0,0,0,.328-.481A5.893,5.893,0,0,0,70.366,46.3Z" transform="translate(-48.844 -17.974)" fill="#253858"/>
                        <circle id="Эллипс_7" data-name="Эллипс 7" cx="2.36" cy="2.36" r="2.36" transform="translate(16.956 23.3)" fill="#253858"/>
                        <path id="Контур_214" data-name="Контур 214" d="M8.784,46.3a3.389,3.389,0,0,1-2.185.787A3.467,3.467,0,0,1,4.414,46.3,5.8,5.8,0,0,0,2.6,50.43a.5.5,0,0,0,.328.481,12.645,12.645,0,0,0,3.671.5c.459,0,.9-.022,1.289-.044a6.848,6.848,0,0,1,1.792-4.042A5.128,5.128,0,0,0,8.784,46.3Z" transform="translate(0 -17.974)" fill="#253858"/>
                        <circle id="Эллипс_8" data-name="Эллипс 8" cx="2.36" cy="2.36" r="2.36" transform="translate(4.239 23.3)" fill="#253858"/>
                        <path id="Контур_215" data-name="Контур 215" d="M37.884,53.2a3.428,3.428,0,0,1-4.37,0A5.893,5.893,0,0,0,31.7,57.352a.5.5,0,0,0,.328.481,13.658,13.658,0,0,0,7.342,0,.473.473,0,0,0,.328-.481A5.725,5.725,0,0,0,37.884,53.2Z" transform="translate(-22.742 -23.367)" fill="#253858"/>
                        <circle id="Эллипс_9" data-name="Эллипс 9" cx="2.36" cy="2.36" r="2.36" transform="translate(10.597 24.808)" fill="#253858"/>
                    </g>
                </svg>`

const icon2 = `<svg xmlns="http://www.w3.org/2000/svg" width="14.788" height="13.238" viewBox="0 0 14.788 13.238">
                    <path id="Контур_212" data-name="Контур 212" d="M-851.544,96.471l-1.556-1.257,1.957.412c.637.134.058,1.214-.4.845Zm-12.633-.175,4.7-5.45a.533.533,0,0,1,.121-.1l.42-1.346a.531.531,0,0,1,.957-.171l1.793,2.687a1.761,1.761,0,0,1,.962-.284,1.769,1.769,0,0,1,1.77,1.77,1.767,1.767,0,0,1-.767,1.458l1.395,2.09a.533.533,0,0,1-.449.88l-1.853-.17a.532.532,0,0,1-.237-.061l-.725.238a2.485,2.485,0,0,1-.9,3.051,2.481,2.481,0,0,1-3.8-1.507l-1.129.371a.527.527,0,0,1-.226.023,1.953,1.953,0,0,1-2.167-3.243.526.526,0,0,1,.137-.232Zm4.489-2.134a1.628,1.628,0,0,1,1.628,1.628,1.628,1.628,0,0,1-1.628,1.628,1.628,1.628,0,0,1-1.628-1.628A1.628,1.628,0,0,1-859.688,94.162Zm-3.225,4.8-.948-1.42A.893.893,0,0,0-862.914,98.964Zm5.8-.8-2.672.878a1.429,1.429,0,0,0,2.2.957,1.423,1.423,0,0,0,.475-1.835Zm-2.026-6.1-4.005,4.648,1.271,1.9,5.828-1.915-3.095-4.637Zm3.331-3.582-.31,1.976-.622-1.9C-856.938,87.94-855.713,87.9-855.8,88.483Zm2.588.788-1.257,1.556.412-1.958C-853.926,88.233-852.846,88.812-853.216,89.271Zm1.848,1.976-1.867.721,1.336-1.49c.435-.484,1.081.557.531.769Zm.612,2.635-1.977-.31,1.9-.621C-850.213,92.749-850.174,93.974-850.757,93.882Z" transform="translate(865.131 -88.069)" fill="#253858" fill-rule="evenodd"/>
                </svg>`

const icon3 = `<svg xmlns="http://www.w3.org/2000/svg" width="11.662" height="13.577" viewBox="0 0 11.662 13.577">
                    <g id="Сгруппировать_765" data-name="Сгруппировать 765" transform="translate(-29.92 -24.397)">
                        <path id="Контур_891" data-name="Контур 891" d="M41.427,29.159l.154-4.025a.721.721,0,0,0-.737-.737l-4.008.171a.639.639,0,0,0-.394.171l-6.355,6.337a.634.634,0,0,0,.051.908l3.854,3.854a.649.649,0,0,0,.908.051l6.355-6.355A.55.55,0,0,0,41.427,29.159Zm-1.781-2.09a.805.805,0,1,1,.805-.805A.8.8,0,0,1,39.645,27.069Z" transform="translate(0 0)" fill="#253858"/>
                        <path id="Контур_892" data-name="Контур 892" d="M41.7,65.092,36.475,70.3c-.171.223-.565.188-.908-.051L32.3,66.993l-.377.548a.651.651,0,0,0,.206.891l4.47,3.117a.645.645,0,0,0,.908-.12l4.316-6.218C41.888,65.126,41.768,65.023,41.7,65.092Z" transform="translate(-1.575 -33.706)" fill="#253858"/>
                    </g>
                </svg>`

const iconArr = [icon1, icon2, icon3]

export default {
    name: 'TabWrapper',
    components: {
        Target, Budget, Audience, RadioBtns
    },
    data () {
        return {
            tabs: ['Influencers', 'Campaign', 'Deal'],
            tabIcon: iconArr
        }
    }
}
</script>

<style scoped lang="scss">
    .wrapper-container {
        margin-top: 20px;
        display: flex;
        flex-direction: column;
        width: 382px;
    }
    .tab-btns {
        display: none;
    }
    .grid {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    @media (min-width: 768px) {
        .wrapper-container {
            max-width: 1316px;
            width: calc(100% - 120px);
            margin-left: 60px;
            margin-right: 60px;
        }
        .tab-btns {
            display: block;
            width: 386px;
        }
        .grid {
            display: grid;
            grid-gap: 15px;
            grid-template-columns: 1fr 1fr;
            align-items: start;
            &::v-deep .grid-item:nth-of-type(1) {
                order: 1;
            }
            &::v-deep .grid-item:nth-of-type(2) {
                order: 3;
            }
            &::v-deep .grid-item:nth-of-type(3) {
                order: 2;
            }
        }
        
    }

</style>
