<template>
  <div class="container">
    <section class="left-section">
	    <v-select
	    	v-model="selectedCountry" 
	    	:items="countries" 
	    	label="Select country" 
	    	>	    	
	    </v-select>
	    <v-btn v-on:click="filterByCountry">Filter by country</v-btn>
	    <v-select
	    	v-model="selectedProxyType" 
	    	:items="proxyTypes" 
	    	label="Select proxyType" 
	    	>	    	
	    </v-select>
	    <v-btn v-on:click="filterByType">Filter by type</v-btn>	  
    	<v-checkbox
      		v-model="isAlive"
      		:label="`alive`">	
    	</v-checkbox>
    	<v-btn v-on:click="filterByAlive">Filter by alive</v-btn>
    </section>
    <v-divider vertical></v-divider>
    <section class="right-section">
      <ul class="main-list" v-for="(proxy, index) in proxydata" :key="index">
        <li class="main-list__item">
          <ul v-for="(value, key) in proxy">
             <li>{{ key }} : {{ value }}</li>
           </ul> 
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
	import axios from 'axios';

	export default {
	    data: () => ({      
	      proxydata: JSON.parse(localStorage.proxydata),
	      countries: [],
	      proxyTypes: [0, 1, 2],
	      selectedCountry: '',
	      selectedProxyType: '',
	      isAlive: ''
	    }),
	    created() {
	      axios.get('http://localhost:8080/api/proxies/?format=json')
	      .then(response => {
	        this.proxydata = response.data;
	        localStorage.setItem('proxydata', JSON.stringify(this.proxydata));
	      	return this.proxydata;
	      })
	      .catch(error => {
	        console.log(error)
	      })
	    },
	   	mounted() {
	   		for (let i = 0; i < this.proxydata.length; i++) {
	   			this.countries.push(this.proxydata[i].country);		
	   		}
	   	},
	   	methods: {
	   		filterByCountry() {
				this.proxydata = JSON.parse(localStorage.proxydata).filter(proxy => proxy.country === this.selectedCountry);
	   		},
	   		filterByType() {
	   			this.proxydata = JSON.parse(localStorage.proxydata).filter(proxy => proxy.proxy_type === this.selectedProxyType);
	   		},
	   		filterByAlive() {
	   			this.proxydata = JSON.parse(localStorage.proxydata).filter(proxy => proxy.alive === this.isAlive);
	   			console.log(this.isAlive);
	   		}
	   	}
	}
</script>

<style>
	body {
	    margin: 0;
	    padding: 0;
	}
	  
	div.container {
	    max-width: 1200px;
	    display: flex;
	    flex-direction: row;
	    justify-content: space-around;
	}

  	section.left-section {
    	width: 300px;
  	}
	
	ul {
	    list-style-type: none;
	}
	
	ul.main-list {
	    border: 1px solid black;
	    padding: 5px;
	}
	
	ul.secondary-list {
	    border: 1px solid black;
	    padding: 5px;
	  }  
</style>