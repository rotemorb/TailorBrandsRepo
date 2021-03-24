<template>
<div class="py-12 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="mt-10">
            <div class="space-y-10 md:space-y-0 md:grid md:grid-cols-2 lg:grid-cols-3 grid-rows-2 md:gap-x-20 md:gap-y-20  grid justify-items-center">
                <div v-for="card in cards" :key="card.id">
                    <card :cardObj="card"></card>
                 </div>   
            </div>
        </div>
    </div>
</div>
</template>

<script >
import axios from 'axios';
import card from './Card.vue'

const apiToken = "keyIGQrpZzTOjhFUM" // use your own key!
const airTableApp = "appgqjxYWLfbBVZQq"
const airTableName = "Content"

export default {
  data() {
    return {
      cards: []
    }
  },
  components:
  {
      card
  },

  // Fetches posts when the component is created.
  created() {


    axios.get(`https://api.airtable.com/v0/${airTableApp}/${airTableName}`,
            { headers: { Authorization: "Bearer " + apiToken }})
        .then((response) => {
            // load the API response into items for datatable
            this.cards = response.data.records.map((item)=>{
                return {
                    id: item.id,
                    ...item.fields
                }
            })
        }).catch((error) => {
            console.log(error)
        })

  }
}
</script>
<style scoped>

</style>