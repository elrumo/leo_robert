<template>
  <div class="app" >

    <NavBar/>

    <section class="grid-col1-2">
        <div class="book-hero-img-wrapper">
          <img class="book-hero-img" :src="books.book1.img2" alt="">
        </div>
      <div class="title-header">
        <h1> {{ books.book1.title }} </h1>
        <h2>
          <!-- <VueMarkdown> -->
            {{ books.book1.description }}
          <!-- </VueMarkdown> -->
        </h2>
        <div class="grid-col-50-50">
          <button>Click Me</button>
          <button>Click Me</button>
        </div>
      </div>
      
    </section>

    <section id="libros" class="books-wrapper-grid">
      <div v-for="book in books" :key="book.title" class="book-wrapper">
          <div v-tilt>
            <img class="book-img" :src="book.img" alt="">
          </div>
          <div>
            <p class="center-x"> {{ book.date }}</p>
            <!-- <button class="center-x">Click Me</button> -->
          </div>
      <!-- {{ book.title }} -->
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
        <button>Click Me</button>
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
import NavBar from './components/NavBar.vue'
// import VueMarkdown from 'vue-markdown'
  // import vanilla_tilt from "vanilla-tilt"
  // console.log(vanilla_tilt);
  

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
              description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam ut aliquam nulla. Vivamus gravida pharetra dolor ac tempor. Maecenas dapibus convallis sem faucibus rutrum. Mauris vehicula pellentesque elit eu vulputate. Etiam placerat libero et nisl sagittis porta. Nullam sed commodo ex, eu aliquet neque.",
              img: require("@/assets/book_1.jpg"),
              img2: require("@/assets/book_1.png"),
              date: "5/10/20"
            },
            book2:{
              title: "Leo y Robert2",
              img: require("@/assets/book_2.jpg"),
              date: "25/10/20",
            },
            book3:{
              title: "Leo y Robert3",
              img: require("@/assets/book_1.jpg"),
              date: "5/11/20",
            },
          }
      }    

    },
    components: {
      // VueMarkdown,
      NavBar,
    }
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
