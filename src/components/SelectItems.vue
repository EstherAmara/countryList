<template>
    <div>
        <h2 class="p-3 bold text-primary">Choose your country, state and city and we'll display your choice</h2>
        <div class="form-group col-md-6 offset-md-3">
            <select
                v-model="chooseCountry"
                @change="selectState(chooseCountry)" 
                class="form-control form-control-lg mt-4 mb-4"  
            >  
                <option 
                v-for="country in countries"
                :value="country.id" 
                :key = country.id> 
                    {{country.name}}
                </option>
            </select>
            
            <select
                v-model="chooseState"
                @change="selectCity(chooseState)"
                class="form-control form-control-lg mt-4 mb-4"  
            >
                <option
                v-for="state in states"
                :key="state.id"
                :value="state.id"
                >
                    {{state.name}}
                </option>
            </select>

            <select
                v-model="chooseCity"
                @change="listDetails(chooseCity)"
                class="form-control form-control-lg mt-4 mb-4"  
            >
                <option
                v-for="city in cities"
                :key="city.id"
                :value="city.id"
                >
                    {{city.name}}
                </option>
            </select>

            <h5 class="text-danger"> {{details}} </h5>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        countries: Array
    },
    data() {
        return {
            states: {},
            cities: {},
            countryName: '',
            stateName: '',
            cityName: '',
            details: '',
        }
    },
    methods: {
        selectState(chooseCountry) {
        const country = this.countries.find((e) => e.id == chooseCountry);
        this.countryName = country.name;
        this.states = country.states;
        },

        selectCity(chooseState) {
            const state = this.states.find((e) => e.id == chooseState);
            this.stateName = state.name;
            this.cities = state.cities;
        },

        listDetails(chooseCity) {
            const city = this.cities.find((e) => e.id == chooseCity);
            this.cityName = city.name;
            this.details = "Your country choice is " + this.countryName + ", state is " + this.stateName + " and city is " + this.cityName;
        }
    },
}
</script>

<style>
    .text-primary {
        color: #065f6d !important;
        font-weight: bolder;
    }
</style>