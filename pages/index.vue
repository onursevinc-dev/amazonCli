<template>
  <main class="listingPage">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-1 col-lg-2 md-3 col-sm-3">
          <!--          Sidebar-->
          <Sidebar class="mb-1" :categories="categories"/>
          <Bar1/>
        </div>
        <!--        Main Contend-->
        <div class="col-xl-11 col-lg-10 md-9 col-sm-9">
          <FeaturedProduct/>

          <div class="mainResults">
            <ul class="s-result-list">
              <li class="s-result-item celwidget" v-for="product in products" :key="product._id">
                <v-card class="mt-3">
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
                          <nuxt-link :to="`/products/${product._id}`">
                            <img :src="product.photo" style="width: 150px" class="img-fluid" alt="">
                          </nuxt-link>
                        </div>
                        <div class="col-sm-5">
                          <div class="a-row a-spacing-small">
                            <!--                          Title and Date-->
                            <nuxt-link :to="`/products/${product._id}`" class="a-link-normal">
                              <h2 class="a-size-medium">
                                {{product.title}}
                                <span class="a-letter-space"></span>
                                <span class="a-letter-space"></span>
                                <span class="a-size-small a-color-secondary">{{getProductDate(product.addedDay)}}</span>
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
<!--                          <div class="row">-->
<!--                            <div class="col-sm-7">-->
<!--                              <div class="a-row a-spacing-none">-->
<!--                                <a href="#" class="a-link-normal a-text-normal">Hardcover</a>-->
<!--                              </div>-->
<!--                            </div>-->
<!--                          </div>-->
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
                            <span class="a-size-small a-color-secondary">Free Cargo</span>
                          </div>
                          <hr>
                          <!--                        other formats-->
<!--                          <span class="a-size-small a-color-secondary">-->
<!--                          Other Formats:-->
<!--                          <span class="a-letter-space"></span>-->
<!--                          <a href="#" class="a-size-small a-link-normal a-text-normal">Audio CD</a>-->
<!--                        </span>-->
                        </div>
                        <div class="col-sm-4">
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
                </v-card>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
  import moment from "moment";
  import FeaturedProduct from "../components/FeaturedProduct";
  import Sidebar from "../components/Sidebar";
  import Bar1 from "../components/Bar1";

  const rating = process.client ? require('vue-rate-it') : {}
  export default {
    name: "index",
    components: {
      Bar1,
      Sidebar,
      FeaturedProduct,
      StarRating: rating.StarRating,
    },
    async asyncData({$axios}) {
      try {
        let responseProducts = $axios.$get("/api/products");
        let responseCategories = $axios.$get("/api/categories");
        const [resProducts, resCategories] = await Promise.all([
          responseProducts,
          responseCategories
        ])
        return {
          products: resProducts.products,
          categories: resCategories.categories
        }
      } catch (err) {
        console.log(err);
      }
    },
    methods: {
      getProductDate(day) {
        let dayr = day.substr(0, 10);
        return moment(dayr).locale("tr").format("Do MMMM dddd YYYY")
      }
    }
  }
</script>

<style>

</style>
