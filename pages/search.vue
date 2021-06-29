<template>
  <main class="listingPage">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-2 col-lg-3 md-4 col-sm-4">
          <!--          Sidebar-->
        </div>
        <!--        Main Contend-->
        <div class="col-xl-10 col-lg-9 md-8 col-sm-8">
          <div class="mainResults">
            <ul class="s-result-list">
              <li class="s-result-item celwidget" v-for="product in products" :key="product.id">
                <div class="s-item-container">
                  <!--                  Best Seller-->
<!--                  <div class="a-spacing-micro">-->
<!--                    <div class="bestSeller">-->
<!--                      <a href="#">Best Seller</a>-->
<!--                    </div>-->
<!--                  </div>-->

                  <div>
                    <div class="row">
                      <div class="col-sm-3 text-center">
                        <nuxt-link :to="`/products/${product.id}`">
                          <img :src="product.photo" style="width: 150px" class="img-fluid" alt="">
                        </nuxt-link>
                      </div>
                      <div class="col-sm-4">
                        <div class="a-row a-spacing-small">
                          <!--                          Title and Date-->
                          <nuxt-link :to="`/products/${product.id}`" class="a-link-normal">
                            <h2 class="a-size-medium">
                              {{product.title}}
                              <span class="a-letter-space"></span>
                              <span class="a-letter-space"></span>
                              <span class="a-size-small a-color-secondary">March 4, 2021</span>
                            </h2>
                          </nuxt-link>
                        </div>
                        <!--                        Author-->
                        <div class="a-row a-spacing-small">
                          <span class="a-size-small a-color-secondary">by</span>
                          <span class="a-size-small a-color-secondary">
                            <a href="#" class="a-link-normal a-text-normal">{{product.owner.name}}</a>
                          </span>
                        </div>
                        <!--                        Shipment-->
                        <div class="a-row">
                          <span class="a-size-small">Ships Turkey</span>
                        </div>
                        <!--                        -->
                        <div class="row">
                          <div class="col-sm-7">
                            <div class="a-row a-spacing-none">
                              <a href="#" class="a-link-normal a-text-normal">Hardcover</a>
                            </div>
                          </div>
                        </div>
                        <!--                        Price-->
                        <div class="a-row a-spacing-none">
                          <a href="#" class="a-link-normal a-text-normal">
                            <span class="a-offscreen">${{product.price}}</span>
                            <span class="a-color-base sx-zero-spacing">
                              <span class="sx-price sx-price-large">
                                <sup class="sx-price-currency">$</sup>
                                <span class="sx-price-whole">{{product.price}}</span>
                                <sup class="sx-price-fractional">00</sup>
                              </span>
                            </span>
                          </a>
                          <span class="a-letter-space"></span>
                          <span class="a-size-base-plus a-color-secondary a-text-strike">${{product.price}}</span>
                        </div>
                        <div class="a-row a-spacing-none">
                          <span class="a-size-small a-color-secondary">Free with audible trial</span>
                        </div>
                        <hr>
                        <!--                        other formats-->
                        <span class="a-size-small a-color-secondary">
                          Other Formats:
                          <span class="a-letter-space"></span>
                          <a href="#" class="a-size-small a-link-normal a-text-normal">Audio CD</a>
                        </span>
                      </div>
                      <div class="col-sm-5">
                        <div class="a-row a-spacing-mini">
                          <!--                          Ratings-->
                          <v-rating
                            empty-icon="far fa-star"
                            full-icon="fas fa-star"
                            half-icon="fas fa-star-half"
                            hover
                            length="5"
                            size="20"
                            readonly
                            half-increments
                            :value="product.averageRating"
                          ></v-rating>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
  const rating = process.client ? require('vue-rate-it') : {}
  export default {
    name: "index",
    components: {
      StarRating: rating.StarRating,
    },
    watchQuery: ["title", "type"],
    async asyncData({$axios, query}) {
      try {
        let products;
        if (query.title) {
          products = await $axios.$post("/api/search", {title: query.title});
        } else if (query.type) {
          products = await $axios.$post("/api/search", {type: query.type});
        }

        return {products}
      } catch (err) {
      }
    }
  }
</script>

<style>

</style>
