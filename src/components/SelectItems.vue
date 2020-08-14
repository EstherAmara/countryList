<template>
    <div>
        <select
            v-model="chooseCountry"
            @change="selectState(chooseCountry)"   
        >  
            <option 
            v-for="country in countries"
            :value="country.id" 
            :key = country.id> 
                {{country.name}} {{country.id}} 
            </option>
        </select>
        
        {{showId}}
        <select
            v-model="chooseState"
            @change="selectCity(chooseState)"
        >
            <option
            v-for="state in states"
            :key="state.id"
            :value="state.id"
            >
                {{state.name}}
            </option>
        </select>

        {{cityId}}
        <select
            v-model="chooseCity"
            @change="listDetails(chooseCity)"
        >
            <option
            v-for="city in cities"
            :key="city.id"
            :value="city.id"
            >
                {{city.name}}
            </option>
        </select>

        {{details}}
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
            this.details = "The Country chosen is " + this.countryName + " and the state chosen is " + this.stateName + " and the city chosen is " + this.cityName;
        }
    },
}
</script>