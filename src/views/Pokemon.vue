<template>
	<div>
    <v-card>
      <v-container
        fluid
        grid-list-lg
      >
        <v-layout row wrap>
		  <v-flex xs12 sm6 md6 lg6 offset-md3 offset-lg3>
            <v-card color="purple" class="white--text">
              <v-layout row class="main-lo">
                <v-flex xs12 md5 offset-md1 offset-lg1>
                  <v-card-title primary-title class="direction">
                    <div class="pok-title">
                      <div class="headline">{{ profile.name }}</div>
                      <br>
                      <v-divider></v-divider>
                      <br>
                    </div>
                    <div class="special" v-if="profile.attacks">
                    	<div class="hard-text">Attacks:</div>
                    	<ul>
                    		<li v-for="attack in profile.attacks">Name: <span class="hard-text">{{attack.name}}</span> <br> Damage: <span class="hard-text">{{attack.damage}}</span></li>
                    	</ul>
                    </div>
                    <div class="special" v-else>
                    	Artist: <span class="hard-text">{{ profile.artist }}</span><br>
                    	Rarity: <span class="hard-text">{{ profile.rarity }}</span><br>
                    	Set: <span class="hard-text">{{ profile.set }}</span><br> 
                    </div>
                  </v-card-title>
                </v-flex>
                <v-flex xs10 md5 offset-xs1 offset-sm1 offset-md0 class="img-order">
                  <v-img class="img-pok"
                    :src="profile.imageUrl"
                    contain
                  ></v-img>
                </v-flex>
              </v-layout>
              <v-divider light></v-divider>
            </v-card>
          </v-flex>
    	</v-layout>
	   </v-container>
	</v-card>
</div>
</template>

<style scoped>
	.pok-title {
		width: 100%;
	}

	.direction {
		flex-direction: row;
	}

	.small {
		font-weight: 500;
	}

	.hard-text {
			font-weight: 600;
		}

	.special {
		margin-top: 5px;
		text-align: left;
	}

	@media only screen and (max-width: 660px) {
		.main-lo {
			flex-direction: column;
		}

		.img-pok {
			width: 100%;
			height: auto;
		}
	}

	@media only screen and (max-width: 992px) {
		/*.img-pok {
			width: 125px;
			height: auto;
		}*/
	}

	@media only screen and (min-width: 992px) {
		.img-pok {
			width: 250px;
			height: auto;
		}

		.hard-text {
			font-weight: 600;
		}
	}
</style>

<script>
	export default {
		data() {
			return {
				id: this.$route.params.id,
				profile: {}
			}
		},
		mounted() {
			this.getProfile()
		},
		methods: {
			getProfile() {
				const uri = 'https://api.pokemontcg.io/v1/cards/' + this.id
				fetch(uri)
				.then(res => res.json())
				.then(data => {
					this.profile = data.card
				}) 
			}
		}
	}
</script>
