<template>
  <div class="text-xs-center">
    <v-pagination
      v-model="page"
      :length="sum"
      @input="paginateData"
      circle
      dark
    ></v-pagination>
  </div>
</template>

<script>
  import EventBus from '../eventBus'
  export default {
	  data () {
	    return {
	      data: {
	        perPage: 10,
	      },
	      page: 1,
	      sum: 0
	    }
	  },
	  methods: {
	    updateData (payload) {
	      this.sum = payload.sum / this.data.perPage
	      console.log(payload.sum)
	    },
	    paginateData () {
	    	EventBus.$emit('PAGE_PUBLISHED', this.page)
	    	console.log(this.page)
	    }
	  },
	  mounted () {
	    EventBus.$on('DATA_PUBLISHED', (payload) => {
	      this.updateData(payload)
	    })
	  }
}
</script>
