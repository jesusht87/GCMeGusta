<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <Startquiz />
    </v-col>
  </v-row>
</template>

<script>
import Startquiz from "../components/startquiz.vue"
export default {
    name: "IndexPage",
    components: { Startquiz }
}
</script>
