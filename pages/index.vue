<template>
  <v-layout>
    <v-flex class="text-center">
      <h1>Welcome, This is {{ title }} Page</h1>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      title: 'Home'
    }
  }
}
</script>
