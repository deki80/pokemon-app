<template>
	<div>
      <v-container
        fluid
        grid-list-lg
      >
        <div row wrap>
		  <v-flex xs12>
		  	<div>
              <h1>Kontaktirajte Nas</h1>
              <br>
              <v-divider></v-divider>
              <br>
            </div>
              <v-layout row class="contact-wrap">
                <v-flex xs7 offset-md1 offset-lg1 class="first">
                    <div>
                		<h2>Škola Koda</h2>
            			<h3>Web Sajt <a href="http://www.skolakoda.org">www.skolakoda.org</a></h3>
            			<h3>Adresa: Čumićevo sokače 2 (Belgrade Design District, I sprat, lokal 87), Terazije</h3>
            			<h3>Beograd</h3>
                    </div>
                </v-flex>
                <v-flex xs5 class="img-order">
                  <img class="img-pok"
                    contain
                    src="@/assets/comp1.png"
                  >
                </v-flex>
              </v-layout>
          </v-flex>
    	</div>
	   </v-container>
</div>
</template>

<style scoped>
	.first {
		margin:0 auto;
	}

	.contact-wrap {
		flex-direction: row;
	}

	@media only screen and (max-width: 620px) {
		.contact-wrap {
		flex-direction: column;
		}
	}
</style>
