<template>
  <v-app>
    <div class="container">

      <v-nav class="nav">
        <div class="left-nav-container">

          <v-icon class="arrow">mdi-arrow-left</v-icon>
          <h4>Back to store</h4>
        </div>

        <img v-if="model == 'yes'" src="./assets/black-switch.png" alt="">
        <img v-else src="./assets/white-switch.png" alt="">

        <v-switch @click="toggleDark" v-model="model" true-value="yes" false-value="no" inset></v-switch>
      </v-nav>
      <hr class="nav-hr">

      <div class="wrapper">


        <div class="product-img">
          <img src="./assets/nocta.png" alt="">
        </div>  

        <div class="product-info">
          <h2 class="product-title">{{ productName }}</h2>
          <div class="top-info">
            <h3>{{ productUse }}</h3>
            <h3>{{ price }}</h3>
          </div>

          <hr class="info-hr">
          <h4 class="product-desc">{{ productDesc }}</h4>

          <div class="sizes">
            <div class="size" v-for="size in  sizes " :key="size"
              :style="{ opacity: size[1] < 1 ? 0.3 : 1, cursor: size[1] < 1 ? 'default' : 'pointer' }">
              <h3>{{ size[0] }}</h3>
            </div>
          </div>

          <div class="quantity-container">
            <div class="quantity-top-info">
              <h2>Quantity</h2>
              <v-icon class="cart" color="white">mdi-cart</v-icon>
            </div>
            <div class="quantity-props">
              <h2 class="quantity-manager" @click="counter--" v-if="counter >= 1">-</h2>
              <h2 class="quantity-manager quantity-counter" v-if="counter >= 1">{{ counter }}</h2>
              <h4 v-else></h4>
              <h2 class="add-quantity" v-on:click="counter++" v-if="counter <= 0">+</h2>
              <h2 class="quantity-manager" v-on:click="counter++" v-if="counter >= 1">+</h2>
            </div>
          </div>

        </div>


      </div>

    </div>
  </v-app>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  transition: all .3s;
}

html {
  font-family: arial;
}

.container {

  @media screen and (max-width: 1230px) {
      h4 {
        display: none;
      }
      @media screen and(max-width: 800px) {
        .product-info{
          display: flex;
          align-self: center;
        }
      }
    }
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  font-family: arial;



  .nav-hr {
    width: 97vw;
    align-self: center;

  }

  .nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    transition: all .2s;




    img {
      width: 50px;
      height: 50px;
    }

    .arrow {
      width: 20px;
      height: 20px;
      cursor: pointer;
    }

    .left-nav-container {
      display: flex;
      margin-left: 10px;

      h4 {
        margin-left: 10px;
        cursor: pointer;
      }
    }

  }

  .wrapper {
    display: flex;
    justify-content: space-between;

    @media only screen and (max-width: 800px) {

      top: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      .product-img {
        background-color: red;
        width: 900px;
        top: 0;
        position: absolute;
        top: 8% !important;
        margin-left: 0px !important;
      }

      .product-info {
        top: -10vh;
      }
      @media screen and(max-width: 440px){
        .product-img{
          width: 400px;
          img{
            width: 398px;
          }
        }
      }
      .product-info{
        max-width: 351px !important;
      }
    }

    .product-img {
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      top: 50%;
      margin-left: 10%;
      max-width: 620px;
      flex-shrink: 5;
      background-color: rgb(255, 255, 255);
      height: 442px;
      border-radius: 20px;
      box-shadow: rgba(0, 0, 0, 0.35) 0px 0px 30px;
      outline: 2px solid black;

      img {
        padding: 20px;
        max-width: 620px;

      }

      @media only screen and (max-width:1230px) {
        display: flex;
        max-width: 520px;
        max-height: 329px;
        top: 70%;

        img {
          max-width: 520px;
          max-height: 342px;
        }
      }

      @media only screen and (max-width: 800px) {

        .product-img {
          top: 0;
          left: 0;
        }
      }
    }

    .product-info {
      position: relative;
      right: 10%;
      top: 10%;
      color: white;
      display: inline-flex;
      flex-direction: column;
      max-width: 700px;
      max-height: 800px;
      width: 600px;
      padding: 10px;
      background-color: rgb(61, 61, 61);
      align-self: flex-end;
      border-radius: 10px;
      box-shadow: rgba(0, 0, 0, 0.35) 0px 0px 30px;

      .product-title {
        text-align: center;
      }

      .info-hr {
        width: 95%;
        align-self: center;
      }

      .top-info {
        display: flex;
        align-items: baseline;
        justify-content: space-between;
        padding: 10px;
      }

      .product-desc {
        margin-top: 10px;
        padding: 5px;
        width: 300px;
        margin-left: 10px;
      }

      .sizes {
        display: flex;
        padding: 10px;

        .size {
          display: flex;
          width: 50px;
          height: 50px;
          align-items: center;
          justify-content: center;
          margin: 10px;
          padding: 20px;
          margin-top: 20px;
          color: white;
          background-color: grey;
          border-radius: 5px;
          cursor: pointer;


          h3 {
            text-align: center;
          }
        }
      }

      .quantity-container {
        display: flex;
        align-self: flex-end;
        flex-direction: column;
        width: 200px;
        height: 90px;
        background-color: rgb(100, 100, 100);
        border-radius: 5px;
        margin: 30px 30px 30px 30px;
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);

        .quantity-top-info {
          display: flex;
          justify-content: space-between;
          width: 200px;
          height: 40px;
          align-items: center;
          padding: 10px;

          h2 {
            margin-left: 35px;
          }

          .cart {
            cursor: pointer;
          }
        }

        .quantity-props {
          display: flex;
          text-align: center;
          align-items: center;
          justify-content: center;
          -webkit-tap-highlight-color: transparent;
          -webkit-touch-callout: none;
          -webkit-user-select: none;
          -khtml-user-select: none;
          -moz-user-select: none;
          -ms-user-select: none;
          user-select: none;


          .quantity-manager {
            padding: 2px;
            margin: 2px 10px 0px 20px;
            cursor: pointer;
          }

          .quantity-counter {
            cursor: default;
          }

          .add-quantity {
            padding: 5px;
            cursor: pointer;
          }
        }
      }

      @media only screen and (max-width: 1230px) {
        .product-info {
          min-width: 420px;
          min-height: 390px;


        }

        .quantity-container {
          align-self: center;
        }

        .product-desc {
          min-width: 200px;
          height: 100px;
          overflow: hidden;
        }
      }

    }
  }
}


</style>

<script>

export default {
  name: 'App',

  data() {
    return {
      price: '$150',
      productName: 'Nike x NOCTA fleece',
      productUse: "Men's Techwear",
      productDesc: "e majority have suffered alteration in some form, by injected humour, or randomised words which don't look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything ",
      sizes: [
        ['S', 12],
        ['M', 1],
        ['L', 0],
        ['XL', 15]
      ],
      counter: 1,
      isDark: true,
      model: 'no'
    }

  },
  methods: {
    toggleDark: function () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      localStorage.setItem("toggleDark", this.$vuetify.theme.dark.toString())
    },

  },

};

</script>
