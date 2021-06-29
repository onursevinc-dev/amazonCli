<template>
  <main>
    <v-card  color="green">
      <v-expansion-panels>
        <v-expansion-panel>
          <v-expansion-panel-header>Bar1</v-expansion-panel-header>
          <v-expansion-panel-content>
<!--            <v-expansion-panel @click="onSearch(category.type)" v-for="category in categories" :key="category._id">-->
            <v-expansion-panel @click="onSearch(category.type)" v-for="category in 10" :key="category">
              <v-expansion-panel-header>
                {{category}}
              </v-expansion-panel-header>
            </v-expansion-panel>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-card>
  </main>
</template>

<script>
  export default {
    name: "Bar1",
    data() {
      return {}
    },
    methods: {
      // onSearch(type) {
      //   this.$router.push({
      //     path: "/search",
      //     query: {type: type}
      //   });
      // }
    }
  }
</script>

<style scoped>

</style>
