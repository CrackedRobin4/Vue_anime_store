<template>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.2/css/bulma.min.css">
  <link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="https://fonts.googleapis.com/css2?family=DotGothic16&display=swap" rel="stylesheet">
  <nav class="navbar has-shadow is-warning">
    <div class="navbar-brand">
      <a class="navbar-item">
        <img src="./assets/Iroha.jpg" alt="logo" style="border-radius: 3px; max-height: 70px;">
        <h3 style="font-family: 'DotGothic16', sans-serif;" class="pl-4">一色 いろはのアニメ店</h3>
      </a>
      <a class="navbar-burger" style="max-height: 70px;" @click="burgerClick">
        <span></span>
        <span></span>
        <span></span>
      </a>
    </div>
    <div class="navbar-menu" id="nav-links">
      <div class="navbar-end">
        <a class="navbar-item">My Account</a>
        <a class="navbar-item" @click="toggleCart">Shopping Cart ({{ cartNum }})</a>
      </div>
    </div>
  </nav>
  <div v-if="showCart">
    <Cart @close="toggleCart" @remove="removeFromCart" :cartNum="cartNum" :price="price"></Cart>
  </div>
  <div v-if="showAdded">
    <Added @closeAdded="toggleAdded"></Added>
  </div>

  <div class="section pt-4 pb-0">
    <nav class="breadcrumb has-arrow-separator">
      <ul class="container">
        <li>
          <a class="has-text-grey">Iroha anime shop</a>
        </li>
        <li>
          <a class="has-text-grey">Figures</a>
        </li>
        <li class="is-active">
          <a>Oregairu</a>
        </li>
      </ul>
    </nav>
  </div>

  <section class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-3">
          <h1 class="is-size-3 title">Yahari Ore no Seishun Love Comedy wa Machigatteiru</h1>
          <h2 class="is-size-4 subtitle">Yui Yuigahama</h2>
        </div>
        <div class="column is-5 has-text-centered">
          <div class="columns is-variable is-0">
            <div class="column is-10">
            <img :src="mainImg" alt="image" style="border-radius: 3px; max-height: 420px;">
          </div>
          <div class="column is-2">
            <ul style="max-height: 460px">
              <li v-for="img in images">
                <img :src="img" @mouseover="mainImg = img" alt="image">
              </li>
            </ul>
          </div>
          </div>
        </div>
        <div class="column is-4">
            <div class="block">
              <h1 class="is-size-4 title">Pop Up Parade My Teen Romantic Comedy SNAFU Climax Yui Yuigahama</h1>
            <h2 class="is-size-5 subtitle">"Yahallo!"</h2>
            </div>
            <div class="block">
              <p>Price: {{ price }}$</p>
            </div>
            <div class="block">
              <p>Available amount: {{ availableItems }}</p>
            </div>
            <div class="block">
              <button class="button is-danger" id="addToCart" @click="addToCart(),toggleAdded()">Add to cart</button>
            </div>
        </div>
      </div>
    </div>
  </section>
  <section class="section">
    <div class="container">
      <div class="column is-8 is-variable">
        <div class="column is-7-tablet">
          <div class="tabs is-boxed">
            <ul>
              <li>
                <a>Product Details</a>
              </li>
              <li>
                Comments
              </li>
            </ul>
          </div>
        </div>
        <div class="column is-5-tablet">
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem dolores, magni, odio ipsam quam architecto eveniet voluptatibus recusandae praesentium facilis iusto aperiam. Modi maiores iusto placeat adipisci alias quasi corrupti?</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Cart from './components/Cart.vue'
import Added from './components/Added.vue'
export default {
  name: 'App',
  components: {
    Cart,
    Added
  },
  data(){
    return{
      cartNum: 0,
      availableItems: 5,
      showCart: false,
      showAdded: false,
      mainImg: require('./assets/Yui/yui_1.jpg'),
      hovered: null,
      images: [
        require('./assets/Yui/yui_1.jpg'),
        require('./assets/Yui/yui_2.jpg'),
        require('./assets/Yui/yui_3.jpg'),
        require('./assets/Yui/yui_4.jpg'),
        require('./assets/Yui/yui_5.jpg'),
        require('./assets/Yui/yui_6.jpg'),
        require('./assets/Yui/yui_7.jpg')
      ],
      price: 38.99,
    }
  },
  methods:{
    burgerClick(){
      document.querySelector('#nav-links').classList.toggle('is-active');
    },
    toggleCart(){
      this.showCart = !this.showCart
    },
    toggleAdded(){
      this.showAdded = !this.showAdded
    },
    addToCart(){
      this.cartNum++
      this.availableItems--
      if(this.availableItems == 0) {
        document.querySelector('#addToCart').setAttribute("disabled", true)
      }
    },
    removeFromCart(){
      this.cartNum--
      this.availableItems++
      if(this.availableItems > 0) {
        document.querySelector('#addToCart').removeAttribute("disabled", true)
      }
    }
  }
}
</script>

<style>
/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
.column .is-2 ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: auto;
}
.column .is-2 ul li img{
  border-radius: 3px; 
  max-height: 60px;
}
.column .is-2 ul li img:hover {
  border: solid orange;
}
@media (max-width:768px){
  .column .is-2 ul li {
    display: block;
    float: left;
    margin-left: auto;
    margin-right: auto;
  }
  .column .is-2 ul li img{
    max-height: 80px;
  }
}
</style>
