<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="member in team" :key="member.id">
      {{ `${member.name} is the ${member.title}` }}
    </div>
  </div>
</template>

<script>
const team = [
  {
    id: 1,
    name: 'failure',
    title: 'fucker'
  },
  {
    id: 2,
    name: 'weirdo',
    title: 'WHOOOOBOOO'
  }
]

export default {
  name: 'Nerd',
  data () {
    return {
      msg: 'Welcome to Your Nerd',
      team: team
    }
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
