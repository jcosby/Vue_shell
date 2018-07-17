<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Example 4</h3>
  Name: <input v-model="name">
  <div>
    Data:
    {{ champion }}
  </div>
  <div>
    Data:
      <div v-for="champion in champions" :key="champion.id">
        {{ champion }}
      </div>
  </div>
  <button @click="getChampions"> Get Champions </button>
  <button @click="getChampionByName">Get Champion By Name </button>
  <hr>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  name: 'Champions',
  data () {
    return {
      msg: 'We are the champions',
      champions: [],
      champion: {}
    }
  },
  methods: {

    async getChampions () {
      try {
        const res = await axios.post(
          'http://localhost:4000/graphql', {
            query: `{ getChampions {
              name
              attackDamage
            }
          }`
          })
        this.champions = res.data.data.getChampions
      } catch (e) {
        console.log('err', e)
      }
    }
  },
  async getChampionByName () {
    const res = await axios.post(
      'http://localhost:4000/graphql', {
        query: `
          query GetChampionByName($championName: String!) {
            getChampionByName(name: $championName) {
              name
              attackDamage
            }
         }`,
        variables: {
          championName: 'Ashe'
        }
      })
    this.champion = res.data.data.getChampionByName
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
