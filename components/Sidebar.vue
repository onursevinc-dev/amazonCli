<template>
  <main>
    <v-card>
      <v-expansion-panels>
        <v-expansion-panel>
          <v-expansion-panel-header>Categories</v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-expansion-panel @click="onSearch(category.type)" v-for="category in categories" :key="category._id">
              <v-expansion-panel-header>
                {{category.type}}
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
    name: "Sidebar",
    props: ["categories"],
    data() {
      return {}
    },
    methods: {
      onSearch(type) {
        this.$router.push({
          path: "/search",
          query: {type: type}
        });
      }
    }
  }
</script>

<style scoped>

</style>
