<template>
    <Rectangle title='Target'>
        <p class="header"><span class="header--bold">45</span> Local influencers available</p>
        <Range title="Followers" :to="600" />
        <Range title="Price rage / post" :from="1" :to="50" />
        <div class="stars-rating">
            <p class="stars-rating__title p">Rating</p>
            <star-rating 
                :show-rating="false"
                :star-size="24"
                active-color="#9637F1"
                :padding="2"
            />
        </div>
        <Accordion
            title="Age and gender"
            subtitle="16 - 65 | All"
        >   
            <div>
                <RadioBtns :btns="gender" shape="square"  color="light-purple"/>
                <Range title="Age" :from="16" :to="65" />
            </div>
        </Accordion>
        <Accordion
            title="Location"
            subtitle="Entire country"
        >
            <!-- <CustomInput
                placeholder="Entire country"
            /> -->
            <select name="" id="" class="custom-select"> 
                <option v-for="loc in location" :key="loc.name" value="loc.name">{{loc.name}}</option>
            </select>
        </Accordion>
        <Accordion
            title="Interests"
            subtitle="All"
        >
            <div class="checkboxes">
                <label class="checkboxes__label">
                    <input 
                        class="checkboxes__input" 
                        type="checkbox"
                        value="all"
                        v-model="checkedInterests"
                    >All
                </label>
                <label class="checkboxes__label">
                    <input
                        class="checkboxes__input" 
                        type="checkbox"
                        value="beauty"
                        v-model="checkedInterests"
                    >Beauty
                </label>
                <label class="checkboxes__label">
                    <input
                        class="checkboxes__input" 
                        type="checkbox"
                        value="blogger"
                        v-model="checkedInterests"
                    >Blogger
                </label>
            </div>
        </Accordion>
        <Accordion
            title="Quality Filters"
            subtitle="All"
        >   
            <div>
                <p>Minimum rating for influencers:</p>
                <star-rating 
                    :show-rating="false"
                    :star-size="24"
                    active-color="#9637F1"
                    :padding="2"
                />
                <p>Collaborations made by influencers:</p>
                <RadioBtns :btns="colobarations" shape="ellips" color="light-purple" />
            </div>
        </Accordion>
    </Rectangle>
</template>

<script>
import Rectangle  from '../ui/Rectangle'
import Range from '../ui/Range'
import RadioBtns from '../ui/RadioBtns'
import CustomInput from '../ui/CustomInput'
import Accordion from '../ui/Accordion'
import StarRating from 'vue-star-rating'

export default {
    name: 'Target',
    components: {
        Rectangle, Range, StarRating, Accordion, RadioBtns, CustomInput
    },
    data () {
        return {
            gender: ['All', 'Women', 'Male'],
            colobarations: ['1+', '5+', '10+'],
            checkedInterests: [],
            location: []
        }
    },
    methods: {
        fetchLocations: function () {
            fetch('http://instars.hostify.one/graphql', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    query: `
                        query NewCampaign{
                            campaignFilterLimits {
                                locations {
                                    name
                                }
                            }
                        }
                        `
                })
            })
            .then((res) => res.json())
            .then((result) => this.location = result.data.campaignFilterLimits.locations)
            .catch(error => console.log(error))
        }
    },
    mounted() {
        this.fetchLocations();
    }
}
</script>

<style scoped lang="scss">
    .header {
        color: #7A828F;
        font-size: 1.56rem;
        font-weight: bold;
        white-space: nowrap;
        margin-left: 19px;
        margin-top: 25px;
        margin-bottom: 33px;
        &--bold {
            font-size: 2.18rem;
            font-weight: 800;
        }
    }
    .stars-rating{
        margin-left: 23px;
        margin-top: 10px;
        &__title {
            font-size: 1rem;
            margin-bottom: 10px;
        }
    }
    .checkboxes {
        width: 100%;
        background: #fff;
        border: 1px solid #D3DaD4;
        border-radius: 8px;
        display: flex;
        flex-direction: column;
        margin-bottom: 10px;
        &__input {
            display: none;
        }
        &__label {
            font-size: 0.875rem;
            padding: 10px;
            border-bottom: 1px solid #D3DaD4;
        }
        &__label:last-of-type {
            border-bottom: none;
        }
    }
    .custom-select {
        width: 100%;
        border: 1px solid #CCD4E0;
        outline: none;
        padding-left: 5px;
        height: 42px;
        margin-bottom: 10px;
    }
</style>
