<template>
  <main>
    <!--  Breadcrumbs-->
    <div class="a-spacing-top-medium"></div>
    <div class="container-fluid">
      <div class="wayfinding-breadcrumbs_container">
        <ul class="a-unordered-list a-horizontal a-size-small">
          <li>
            <span class="a-list-item">
              <nuxt-link :to="`/search?type=${product.category.type}`" class="a-link-normal a-color-tertiary">{{product.category.type}}</nuxt-link>
            </span>
          </li>
          <li>
            <span class="a-list-item">></span>
          </li>
          <li>
            <span class="a-list-item">
              <nuxt-link :to="`/search?title=${product.title}`"
                         class="a-link-normal a-color-tertiary">{{product.title}}</nuxt-link>
            </span>
          </li>
        </ul>
      </div>
    </div>
    <div class="container-fluid">
      <div class="dp-container">
        <div class="row">
          <!--          First 3 col Product İmage and Author-->
          <div class="col-lg-3 col-md-3 col-sm-4">
            <div class="leftCol">
              <!--              Image-->
              <div class="imgBlock">
                <div class="eBooksimg">
                  <img :src="product.photo" class="img-fluid" alt="">
                </div>
              </div>
              <!--              Follow Author-->
              <div class="authorFollow">
                <hr class="a-divider-normal">
                <h1 class="authorFollowHeading">Follow The Author</h1>
                <div class="a-spacing-top-small">
                  <div class="row">
                    <!--                      Author's İmage-->
                    <div class="col-xl-3 col-lg-3 col-md-3 col-sm-3 col-3">
                      <div class="smallAuthorImageContainer">
                        <a href="#">
                          <img :src="product.owner.photo" alt="" class="img-fluid">
                        </a>
                      </div>
                    </div>
                    <!--                      Author's Name-->
                    <div class="col-xl-4 col-lg-3 col-md-3 col-sm-3 col-3">
                      <div class="authorNameCol">
                        <a href="#" class="">{{product.owner.name}}</a>
                      </div>
                    </div>
                    <!--                      Author's Follow Buttons-->
                    <div class="col-xl-5 col-lg-6 col-md-6 col-sm-6 col-6">
                      <div class="authorBtn mt-2">
                        <a href="#">
                              <span class="btnFollow">
                                <span class="a-btn-inner">
                                  <button class="a-btn-text">+ Follow</button>
                                </span>
                              </span>
                        </a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!--          Middle 6 col Description-->
          <div class="col-lg-6 col-md-6 col-sm-8">
            <div class="centerCol">
              <!--              Product Title-->
              <div class="titleDiv">
                <h1 class="productTitle">
                  <span class="largeTitle">{{product.title}}</span>
                  <!--                  <span class="smallTitle">Paperback</span>-->
                </h1>
              </div>
              <!--              Author's Name-->
              <div class="bylineinfo">
                by
                <a href="#" class="authorName">
                  {{product.owner.name}}
                </a>(Author)
              </div>
              <div class="reviewGroup">
                <!--                ReviewGroup-->
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
              <hr style="margin-top: 10px">
              <!--                A tags Dummy data-->
              <div class="mediaMatrix">
                <div class="formats">
                  <a href="#" class="link-expander">>
                    <span class="tmmShowPrompt">See all 18 formats and editions</span>
                  </a>
                  <div>
                    <!--                  <ul>-->
                    <!--                    &lt;!&ndash;                      Kindle&ndash;&gt;-->
                    <!--                    <li class="swatchElement" style="width: 117px">-->
                    <!--                        <span class="a-list-item">-->
                    <!--                          <span class="a-button-toggle">-->
                    <!--                            <span class="a-button-inner">-->
                    <!--                              <a href="#" class="a-button-text">-->
                    <!--                                <span class="">Kindle</span>-->
                    <!--                                <br>-->
                    <!--                                <span class="a-color-secondary">-</span>-->
                    <!--                              </a>-->
                    <!--                            </span>-->
                    <!--                          </span>-->
                    <!--                        </span>-->
                    <!--                      <span class="tmm-olp-links"></span>-->
                    <!--                      <span class="tmm-olp-links">-->
                    <!--                          <a href="#" class="a-size-mini">-->
                    <!--                            <span class="kcpAppBox">-->
                    <!--                              <span class="a-declarative">-->
                    <!--                                Read with our-->
                    <!--                                <span class="a-text-bold">Free App</span>-->
                    <!--                              </span>-->
                    <!--                            </span>-->
                    <!--                          </a>-->
                    <!--                        </span>-->
                    <!--                    </li>-->
                    <!--                    &lt;!&ndash;                      Audible&ndash;&gt;-->
                    <!--                    <li class="swatchElement" style="width: 117px">-->
                    <!--                        <span class="a-list-item">-->
                    <!--                          <span class="a-button-toggle">-->
                    <!--                            <span class="a-button-inner">-->
                    <!--                              <a href="#" class="a-button-text">-->
                    <!--                                <span class="">-->
                    <!--                                  <img src="/img/audibleLogo.png" class="img-fluid" style="width: 20px" alt="">-->
                    <!--                                  Audible-->
                    <!--                                </span>-->
                    <!--                                <br>-->
                    <!--                                <span class="a-color-secondary">-</span>-->
                    <!--                              </a>-->
                    <!--                            </span>-->
                    <!--                          </span>-->
                    <!--                        </span>-->
                    <!--                      <span class="tmm-olp-links"></span>-->
                    <!--                      <span class="tmm-olp-links">-->
                    <!--                          <a href="#" class="a-size-mini">-->
                    <!--                            <span class="kcpAppBox">-->
                    <!--                              <span class="a-declarative">-->
                    <!--                                <span class="a-text-bold">Free App</span> with your try Audible trial-->
                    <!--                              </span>-->
                    <!--                            </span>-->
                    <!--                          </a>-->
                    <!--                        </span>-->
                    <!--                    </li>-->
                    <!--                    &lt;!&ndash;                      Paperback&ndash;&gt;-->
                    <!--                    <li class="swatchElement" style="width: 117px">-->
                    <!--                        <span class="a-list-item">-->
                    <!--                          <span class="a-button-toggle">-->
                    <!--                            <span class="a-button-inner">-->
                    <!--                              <a href="#" class="a-button-text">-->
                    <!--                                <span class="">Paperback</span>-->
                    <!--                                <br>-->
                    <!--                                <span class="a-color-secondary">-</span>-->
                    <!--                              </a>-->
                    <!--                            </span>-->
                    <!--                          </span>-->
                    <!--                        </span>-->
                    <!--                    </li>-->
                    <!--                  </ul>-->
                  </div>
                </div>
              </div>
              <!--              Description-->
              <div class="bookDescription">
                <div class="bookDescriptionInner">
                  {{product.description}}
                </div>
              </div>
              <!--              Product specification-->
              <!--              <div class="aboutEbooksFeature">-->
              <!--                <hr>-->
              <!--                <div class="row">-->
              <!--                  <div class="col-sm-4 mb-1">-->
              <!--                    <div class="a-declarative">-->
              <!--                      Length <span><a href="#">386 pages <i class="a-icon a-icon-popover"></i></a></span>-->
              <!--                    </div>-->
              <!--                  </div>-->
              <!--                </div>-->
              <!--              </div>-->
            </div>
          </div>
          <!--          Last 3 col Buying Section-->
          <div class="col-lg-3 col-md-3 col-sm-6">
            <div class="combinedBuyBox">
              <div class="buyBox">
                <div class="a-section">
                  <div class="clearfix">
                    <div class="float-left">
                      <form>
                        <input type="radio" id="test1" name="radio-group checked"/>
                        <label for="test1">Buy Now</label>
                      </form>
                    </div>
                    <!--                    Product Price-->
                    <div class="float-right">
                      <span class="a-size-medium a-color-price a-text-normal">
                        ${{product.price}}
                      </span>
                    </div>

                  </div>
                </div>
                <div class="a-section a-spacing-none">
                  <div class="row">
                    <div class="col-sm-5 col-5">
                      <label>
                        <select>
                          <option v-for="i in 10" :key="i" :value="i">Qty &nbsp; {{i}}</option>
                        </select>
                      </label>
                    </div>
                  </div>
                </div>
                <div class="a-section a-spacing-small a-spacing-top-micro">
                  <div class="row">
                    <span class="a-color-base buyboxShippingLabel"></span>
                  </div>
                </div>
                <div class="a-section a-spacing-small">
                  <div class="a-section a-spacing-none">
                    <span class="a-size-medium a-color-success">In Stock</span>
                  </div>
                  <div class="a-section a-spacing-mini">Ships from and sold by Amazon.com</div>
                </div>
                <div class="a-section">
                  <div class="a-button-stack" @click="addProductToCart(product)">
                    <span class="a-spacing-small a-button-primary a-button-icon">
                      <span class="a-button-inner">
                        <i class="a-icon a-icon-cart"></i>
                        <input type="submit" class="a-button-input" name="submit.add-to-cart">
                        <span class="a-button-text">Add to Cart</span>
                      </span>
                    </span>
                  </div>
                  <div class="a-button-stack" @click="goBuyProduct">
                    <span class="a-spacing-small a-button-primary a-button-icon">
                      <span class="a-button-inner">
                        <i class="a-icon a-icon-buynow"></i>
                        <input type="submit" class="a-button-input" name="submit.add-to-cart">
                        <span class="a-button-text">Buy Now</span>
                      </span>
                    </span>
                  </div>
                </div>
                <div class="a-row">
                  <div class="a-spacing-top-small">
                    <div class="a-section a-spacing-none">
                      <div class="a-section a-spacing-none a-spacing-top-mini">
                        This İtem Ships to
                        <b>California</b>
                        <b>Get it by Monday, March 1 - Monday, March 8</b>
                        Chose this date at checkout
                      </div>
                    </div>
                  </div>
                </div>
                <hr>
                <span class="a-declarative">
                  <a href="#" class="a-link-normal">
                    <div class="a-row a-spacing-mini">
                      <i class="fal fa-map-marked-alt"></i>
                      <span class="a-size-small">Deliver to California</span>
                    </div>
                  </a>
                </span>
                <br>
                <hr>
                <div class="a-section">
                  <div class="clearfix">
                    <div class="float-left">
                      <form>
                        <input type="radio" id="test2" name="radio-group">
                        <label for="test2">Buy Now</label>
                      </form>
                    </div>
                    <div class="float-right">
                      <span class="a-color-base offer-price a-text-normal">${{product.price}}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="kcpAppBaseBox text-center">
              <img src="/img/readyondevice.png" class="img-fluid" alt="">
            </div>
          </div>
        </div>
        <br>
        <hr>
        <div class="books-entity-teaser">
          <div class="bucket">
            <h2>More about the Author</h2>
            <div class="content">
              <div class="row">
                <!--                Author's photo and button-->
                <div class="col-md-2 col-sm-4 col-4">
                  <div class="authorContent">
                    <div class="authorImageSingle">
                      <a href="#">
                        <img :src="product.owner.photo" alt="" class="img-fluid">
                      </a>
                    </div>
                    <div class="authorFollowHeading">
                      <button class="followButton" type="button">
                        <span class="pr-fb-icon"></span>
                        <span class="pr-fb-text">Follow</span>
                      </button>
                    </div>
                  </div>
                </div>
                <!--                Author's About-->
                <div class="col-md-10 col-sm-8 col-8 pl-0">
                  <div class="mainContent">
                    <h3>Biography</h3>
                    <div id="authorBio">{{product.owner.about}}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-4">
            <h2>
              Ürün Teknik Özellikleri
            </h2>
            <template>
              <v-simple-table>
                <template v-slot:default>
                  <thead>
                  <tr>
                    <th class="text-left">
                      {{product.title}}
                    </th>
                    <th class="text-left">
                      Teknik Özellikleri
                    </th>
                  </tr>
                  </thead>
                  <tbody>
                  <tr>
                    <td>Ekran</td>
                    <td>1920x1080 LCD Ekran</td>
                  </tr>
                  <tr>
                    <td>Dokunmatik Ekran</td>
                    <td>Var</td>
                  </tr>
                  <tr>
                    <td>Cd Rom</td>
                    <td>Yok</td>
                  </tr>
                  </tbody>
                </template>
              </v-simple-table>
            </template>
          </div>
          <div class="col-4"><h1>Benzer Satıcılar</h1></div>
          <div class="col-4"><h1>Size Önerilenler</h1></div>
        </div>
        <!--        Review Section-->
        <ReviewSection :product="product" :reviews="reviews"/>
      </div>
    </div>
  </main>
</template>

<script>
  import {mapActions} from 'vuex';

  const rating = process.client ? require('vue-rate-it') : {}
  import ReviewSection from "../../components/ReviewSection";

  export default {
    components: {
      StarRating: rating.StarRating,
      ReviewSection,
    },
    async asyncData({$axios, params}) {
      try {
        let responseProduct = $axios.$get(`/api/products/${params.id}`);
        let responseReviews = $axios.$get(`/api/review/${params.id}`);

        const [productResponse, reviewsResponse] = await Promise.all([
          responseProduct,
          responseReviews
        ]);
        return {
          product: productResponse.product,
          reviews: reviewsResponse.reviews
        }
      } catch (err) {
        console.log(err);
      }
    },
    data() {
      return {
        //
      }
    },
    methods: {
      ...mapActions(["addProductToCart"]),
      goBuyProduct() {
        this.$router.push("/payment");
      }
    }
  }
</script>

<style scoped>

</style>
