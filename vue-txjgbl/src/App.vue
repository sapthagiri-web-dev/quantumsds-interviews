<template>
  <div id="app">
    <h2>Country detail app</h2>
    <div>
      <div class="countryDropdown">
        <select name="cars" id="cars" class="name-input dropdown">
          <option  v-for="countries in countryList">
            {{ countries.name }}
          </option>
        </select>
       <p>country information by :  {{inputValue}}</h2>
        <h3>Iso Code</h3>
      </div>

      <div class="name-input">
        <input
          type="text"
          class="name-input"
          placeholder="name input"
          v-model="inputValue"
        />
        <h3>currency</h3>
      </div>
    </div>
    <div class="state-name-search">

          <input
          type="text"
          class="name-input"
   placeholder="state name search"
          v-model="stateName"
        />
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },

  data() {
    return {
      countryList: [],
      inputValue: '',
      stateNames : [],
      stateName:''
    };
  },

  mounted() {
    // fetch('https://countriesnow.space/api/v0.1/countries/iso')
    //   .then((response) => response.json())
    //   .then((data) => {
    //     this.countryList = data.data;
    //   });


    fetch('https://countriesnow.space/api/v0.1/countries/states')
    .then((response) => response.json())
    .then((data) => { this.stateNames = data.data });


  },

  watch: {
    inputValue(val) {
      console.log(val);
    },

    stateName(val){
      console.log(this.stateNames,'stateNames')
      
    }
  },

  // methods: {
  //   nameInput(e) {
  //     console.log(e);
  //   },
  // },

  //   fetch('https://countriesnow.space/api/v0.1/countries/currency ')
  //     .then((response) => response.json())
  //     .then((data) => console.log(data));
  // },
  // fetch('https://countriesnow.space/api/v0.1/countries/states')
  //   .then((response) => response.json())
  //   .then((data) => console.log(data));
};
</script>

<style>
h2 {
  text-align: center;
  color: #2c3e50;
}
.countryDropdown,
.name-input {
  display: flex;
  justify-content: space-around;
}

.name-input {
  height: 20px;
}

.state-name-search {
  display: flex;
  justify-content: center;
  margin-top: 100px;
}
.dropdown {
  width: 40%;
}
</style>
