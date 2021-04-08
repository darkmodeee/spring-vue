<template>
  <div class="home">
    <HelloWorld msg="Welcome to Spring-Vue App"/>
    <button @click="hello">hello</button>
    {{response}}
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data () {
    return {
      response: '',
      errors: []
    }
  },
  methods: {
    hello () {
      axios.get('/api/hello')
        .then(res => {
          this.response = res.data
        }).catch(err => this.errors.push(err))
    }
  }
}
</script>
