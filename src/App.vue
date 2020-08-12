<template>
  <div class="app" >

    <NavBar/>

    <!-- Hero section -->
    <section class="grid-col1-2">
        <div class="book-hero-img-wrapper">
          <img class="book-hero-img" :src="books.book1.img2" alt="">
        </div>
      <div class="title-header">
        <h1> {{ books.book1.title }} </h1>
        <h2 style="font-size: 1.1rem;">
          {{ books.book1.description }}
          <!-- <markdown-it-vue class="md-body" :content="books.book1.description"/> -->
        </h2>
        <!-- Signup form -->
        <div id="mc_embed_signup">
          <!-- Begin Mailchimp Signup Form -->
          <!-- <link href="//cdn-images.mailchimp.com/embedcode/classic-10_7.css" rel="stylesheet" type="text/css"> -->
          <!-- <style type="text/css">
            #mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
            /* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
              We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
          </style> -->
          <form action="https://gmail.us17.list-manage.com/subscribe/post?u=e3081c2a7a7b22d3f511a0e72&amp;id=b7d9d9c042" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
          <div id="mc_embed_signup_scroll">
            <!-- <h2>¡Recuérdame cuando esté en venta!</h2> -->

            <div class="input-grid">
              <input type="email" value="" name="EMAIL" class="email-box" placeholder="Tu correo electrónico" id="mce-EMAIL">
            
              <div style="position: absolute; left: -5000px;" aria-hidden="true">
                <input type="text" name="b_e3081c2a7a7b22d3f511a0e72_b7d9d9c042" tabindex="-1" value="">
              </div>

              <div class="clear">
                <input type="submit" value="¡Recuérdame cuando esté en venta!" name="subscribe" id="mc-embedded-subscribe" class="outline input-btn">
              </div>
            </div>
              
            <div id="mce-responses" class="clear">
              <div class="response" id="mce-error-response" style="display:none"></div>
              <div class="response" id="mce-success-response" style="display:none"></div>
            </div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
          </div>
          </form>
        </div>

        <!-- <button class="filled">¡Recuérdame cuando esté en venta!</button> -->
        <!-- <div class="grid-col-50-50">
          <div class="dropdown">
            <button class="filled">Comprar por 2,99€</button>
            <div class="dropdown-content">
              
              <div class="purchase-option-wrapper">
                <a href="#">
                  <img SameSite="None" src="https://i.imgur.com/nFf49RA.png" alt="">
                </a>
              </div>
              
              <div class="purchase-option-wrapper">
                <a href="#">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Rakuten_Kobo_Logo_2019.svg/440px-Rakuten_Kobo_Logo_2019.svg.png" alt="">

                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a href="#">
                  <img SameSite="None" src="https://i.imgur.com/qYholOb.png" alt="">
                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a href="#">
                  <img SameSite="None" src="https://tools.applemediaservices.com/api/badges/get-it-on-apple-books/badge/es-ES?size=250x83&releaseDate=1583193600" alt="">
                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a href="#">
                  <img SameSite="None" src="https://i.imgur.com/Zjqmef1.png?1" alt="">
                </a>
              </div>

            </div>
          </div>
          <button class="outline">Lee el primer capitulo</button>

        </div> -->

      </div>
      
    </section>

    <!-- Signup form -->
   

    <!--End mc_embed_signup-->

    <section id="libros" class="books-wrapper-grid">
      <div v-for="book in books" :key="book.title" class="book-wrapper">
        <div v-if="book.isBlur" class="blur">
          <div>
            <img class="book-img" :src="book.img" alt="">
          </div>
          <div>
            <p class="center-x" style="padding-bottom: 5px; padding-top: 10px; font-weight: bold;"> Preventa: </p>
            <p class="center-x">  {{ book.date }}</p>
          </div>
        </div>

        <div v-if="!book.isBlur" class="">
          <div v-tilt>
            <img class="book-img" :src="book.img" alt="">
          </div>
          <div>
            <p class="center-x" style="padding-bottom: 5px; padding-top: 10px; font-weight: bold;"> Preventa: </p>
            <p class="center-x">  {{ book.date }}</p>
          </div>
        </div>
      </div>
    </section>

    <section id="autora" class="grid-col2-1 margin-top-lg">
      <div class="title-header">
        <h1>Reginah <br> George</h1>
        <h2>
          <!-- <VueMarkdown> -->
            {{ text.homeIntro }}
          <!-- </VueMarkdown> -->
        </h2>
        <a href="#libros">
        <button class="filled">Mis libros</button>
        </a>
      </div>
      <div class="author-img-wrapper">
        <img class="author-img" src="@/assets/reginah.jpg" alt="">
      </div>
    </section>
    
    <footer>

      <h5>
        Illustration by <a class="underline" target="_blank" href="https://www.instagram.com/ariadnadraws/"> Ariadna </a>
      </h5>
      <h5>
        Web made with ♥️ by <a class="underline" target="_blank" href="https://eliasruiz.com/"> Elias Ruiz </a>
      </h5>

    </footer>


  </div>
</template>

<script>
import firebase from './firebase.js'
import NavBar from './components/NavBar.vue'
// import MarkdownItVue from 'markdown-it-vue'

import 'markdown-it-vue/dist/markdown-it-vue.css'

  export default {
    name: 'app',

    data(){
        return {
          text:{
            homeIntro: "¡Hola! Me llamo Reginah y he escrito “Leo y Robert”, una trilogía de dos chicos y un amor imposible dentro de una editorial. ¡Haz click en las portadas para descubrir más!",
          },
          books:{
            book1:{
              title: "Leo y Robert",
              description: '"Por lo tanto, y después de haberlo reflexionado tras estos años, he llegado a la conclusión de que tú y yo llegásemos a cruzarnos aquel día resultó ser un maravilloso milagro."',
              img: require("@/assets/book_1.jpg"),
              img2: require("@/assets/book_1.png"),
              date: "8 Septiembre 2020",
              isBlur: false
            },
            book2:{
              title: "Leo y Robert2",
              img: require("@/assets/book_2.jpg"),
              date: "8 Septiembre 2020",
              isBlur: true
            },
            book3:{
              title: "Leo y Robert3",
              img: require("@/assets/book_3.jpg"),
              date: "8 Septiembre 2020",
              isBlur: true
            },
          },
      }    

    },
    components: {
      NavBar,
      // MarkdownItVue,
    },
  }
</script>

<style>
  @import "~@/app.css";

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
</style>
