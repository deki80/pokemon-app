<template>
  <div id="home">
	<v-card>
      <v-container
        fluid
        grid-list-lg
      >
        <v-layout row wrap>
		  <v-flex xs12 sm6 md4 lg4 v-for="pokemon in pokemons">
            <v-card color="purple" class="white--text">
              <v-layout row>
                <v-flex xs7>
                  <v-card-title primary-title>
                    <div>
                      <div class="headline">{{pokemon.name}}</div>
                      <div class="textual">Series: {{pokemon.series}}</div>
                      <div></div>
                    </div>
                  </v-card-title>
                </v-flex>
                <v-flex xs5>
                  <v-img
                    :src="pokemon.imageUrl"
                    height="125px"
                    contain
                  ></v-img>
                </v-flex>
              </v-layout>
              <v-divider light></v-divider>
              <v-card-actions class="pa-3">
                <v-btn flat color="orange" @click="profilePage(pokemon.id)">
            	  More Info
            	</v-btn>
                <v-spacer></v-spacer>
              </v-card-actions>
            </v-card>
          </v-flex>
    	</v-layout>
    	<div class="text-xs-center">
	      <v-pagination
	        v-model="page"
	        :length="5"
	        @input="paginate"
	        circle
	        dark
	      ></v-pagination>
  		</div>
	   </v-container>
	</v-card>
  </div>
</template>

<style>
	.textual {
		font-weight: 800;
		font-family: Helvetica;
		font-size:16px;
	}
</style>

<script>
	export default {
		data() {
			return {
				pokemons: [],
				allPokemons: [],
				page: 1,
				perPage: 10
			}
		},
		mounted() {
			this.getPokemons()
		},
		methods: {
    	  getPokemons () {
      	    const uri = 'https://api.pokemontcg.io/v1/cards'
      	    fetch(uri)
			.then(res => res.json())
			.then(data => {
				//this.pokemons = data.cards
				this.allPokemons = data.cards
				this.pokemons = this.allPokemons.slice((this.page - 1) * this.perPage, this.page * this.perPage)
			})
    	  },
    	  paginate() {
    	  	this.pokemons = this.allPokemons.slice((this.page - 1) * this.perPage, this.page * this.perPage)
    	  	window.scrollTo(0,0);
    	  },
        profilePage(pokemonId) {
          this.$router.push({ name: 'pokemon', params: {id: pokemonId}})
        }
  		}
	}
</script>
