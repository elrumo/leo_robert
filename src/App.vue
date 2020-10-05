<template>
  <div class="app" >

    <NavBar/>

    <modal class="book-dialog" name="book-dialog">
      <div class="dialog-grid">
        <div class="dialog-image">
          <img class="book-image-dialog" :src="dialogWindow.img" alt="">
        </div>
        <div class="dialog-info-grid">
          <h1 class="dialog-h1" > <vue-markdown> {{ dialogWindow.title }} </vue-markdown></h1>
          <h2 class="dialog-h2">
            <vue-markdown :html="true"> {{ dialogWindow.description }} </vue-markdown>
          </h2>
          <div class="modal-btns-grid" style="max-width:580px">
            <div class="dropdown float-left">
              <button class="filled">Comprar por 2,99€</button>
              <div class="dropdown-content dropdown-content-dialog">
                
                <div class="purchase-option-wrapper">
                  <a target="_blank" :href="dialogWindow.links.amazon">
                    <img SameSite="None" src="https://i.imgur.com/nFf49RA.png" alt="">
                  </a>
                </div>
                
                <div class="purchase-option-wrapper">
                  <a target="_blank" :href="dialogWindow.links.kobo">
                      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Rakuten_Kobo_Logo_2019.svg/440px-Rakuten_Kobo_Logo_2019.svg.png" alt="">

                  </a>
                </div>

                <div class="purchase-option-wrapper">
                  <a target="_blank" :href="dialogWindow.links.casa">
                    <img SameSite="None" src="https://i.imgur.com/qYholOb.png" alt="">
                  </a>
                </div>

                <div class="purchase-option-wrapper">
                  <a target="_blank" :href="dialogWindow.links.apple">
                    <img SameSite="None" src="https://tools.applemediaservices.com/api/badges/get-it-on-apple-books/badge/es-ES?size=250x83&releaseDate=1583193600" alt="">
                  </a>
                </div>

                <div class="purchase-option-wrapper">
                  <a target="_blank" :href="dialogWindow.links.play">
                    <img SameSite="None" src="https://i.imgur.com/Zjqmef1.png?1" alt="">
                  </a>
                </div>

              </div>
            </div>

            <a v-if="isBook1" class="float-left" target="_blank" href="https://www.megustaleer.com/libros/leo-y-robert-1150-libro-1-leo-y-robert-1/MES-113043/fragmento">
              <button class="outline">Lee el primer capítulo</button>
            </a>

            <a class="goodreads-wrapper float-left" target="_blank" :href="dialogWindow.links.goodreads">
              <img :src="goodreads" alt="">
            </a>

          </div>
        </div>
      </div>
    </modal>

    <!-- Hero section -->
    <section class="grid-col1-2">
        <div class="book-hero-img-wrapper">
          <img class="book-hero-img" :src="mainBook" alt="">
        </div>
      <div class="title-header">
        <h1> {{ books.book1.title }} </h1>
        <h2>
          <vue-markdown> {{ books.book1.description }} </vue-markdown>
        </h2>
        <!-- Signup form -->
        <!-- <button class="filled">¡Recuérdame cuando esté en venta!</button> -->
        <div class="grid-col-50-50">
          <div class="dropdown">
            <button class="filled">Comprar por 2,99€</button>
            <div class="dropdown-content">
              
              <div class="purchase-option-wrapper">
                <a target="_blank" href="https://www.amazon.es/shop/theboyinneon">
                  <img SameSite="None" src="https://i.imgur.com/nFf49RA.png" alt="">
                </a>
              </div>
              
              <div class="purchase-option-wrapper">
                <a target="_blank" href="https://www.kobo.com/es/es/search?query=reginah%20george&fcsearchfield=Author">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Rakuten_Kobo_Logo_2019.svg/440px-Rakuten_Kobo_Logo_2019.svg.png" alt="">

                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a target="_blank" href="https://www.casadellibro.com/?q=Reginah%20George">
                  <img SameSite="None" src="https://i.imgur.com/qYholOb.png" alt="">
                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a target="_blank" href="https://books.apple.com/es/author/reginah-george/id1531527468">
                  <img SameSite="None" src="https://tools.applemediaservices.com/api/badges/get-it-on-apple-books/badge/es-ES?size=250x83&releaseDate=1583193600" alt="">
                </a>
              </div>

              <div class="purchase-option-wrapper">
                <a target="_blank" href="https://play.google.com/store/books/author?id=Reginah+George&hl=es">
                  <img SameSite="None" src="https://i.imgur.com/Zjqmef1.png?1" alt="">
                </a>
              </div>

            </div>
          </div>

          <a target="_blank" href="https://www.megustaleer.com/libros/leo-y-robert-1150-libro-1-leo-y-robert-1/MES-113043/fragmento">
            <button class="outline">Lee el primer capítulo</button>
          </a>

        </div>

      </div>
      
    </section>


    <section id="libros" class="books-wrapper-grid">
      <div @click="show(book.isBook)" v-for="book in books" :key="book.title" class="book-wrapper">
        <div v-if="book.isBlur" class="blur">
          <div>
            <img class="book-img" :src="book.img" alt="">
          </div>
          <div>
            <p class="center-x" style="padding-bottom: 8px; padding-top: 10px; font-weight: bold;"> ¡Ya en preventa!</p>
            <p class="center-x">  {{ book.date }}</p>
          </div>
        </div>

        <div v-if="!book.isBlur" class="">
          <div >
            <img class="book-img" :src="book.img" alt="">
          </div>
          <div>
            <p class="center-x" style="padding-bottom: 5px; padding-top: 10px; font-weight: bold;"> ¡Ya en preventa! </p>
            <p class="center-x"> Publicación: {{ book.date }}</p>
          </div>
        </div>
      </div>
    </section>

    <section id="autora" class="grid-col2-1 margin-top-lg">
      <div class="title-header">
        <h1>Reginah <br> George</h1>
        <h2 class="bio-text">
          <vue-markdown> {{ text.homeIntro }} </vue-markdown>
        </h2>
        <div class="social-icons-wrapper">
            <a v-for="icon in icons" :key="icon.name" target="_blank" class="nav-hover social-icon-reginah" :href="icon.url">
                <img class="social-icon" :src="icon.img" alt="">
            </a>
        </div>
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
// import firebase from './firebase.js'
import NavBar from './components/NavBar.vue'
import VueMarkdown from 'vue-markdown'
// import VModal from 'vue-js-modal'


  export default {
    name: 'app',

    data(){
        return {
          isBook1: false,
          isBook2: false,
          isBook3: false,
          mainBook: require("@/assets/book_1.png"),
          text:{
            homeIntro: "Me llamo Reginah, tengo 24 años y vivo en California, en un aburrido barrio de casas blancas donde nunca pasa nada interesante y siempre huele a césped recién cortado. Adoro los libros, la limonada recién hecha y a Lana del Rey. Cuando me aburro, escribo historias como las que me gustaría leer: llenas de personajes distintos, con problemas del día a día y la esperanza de encontrar el amor. La pregunta es... ¿dejaré que eso ocurra o se lo pondré algo difícil? <br><br> Mi primera trilogía, «Leo y Robert», se publica en otoño/invierno de 2020, ¡no os la podéis perder!",
          },
          goodreads: require("@/assets/add_to_goodreads.svg"),
          books:{
            book1:{
              title: "Leo y Robert",
              description: '"Descubre la trilogía "Leo y Robert", escrita por la prometedora escritora californiana Reginah George. Ya disponible en todas las plataformas y librerías digitales"',
              // description: '"Por lo tanto, y después de haberlo reflexionado tras estos años, he llegado a la conclusión de que tú y yo llegásemos a cruzarnos aquel día resultó ser un maravilloso milagro."',
              img: require("@/assets/book_1.jpg"),
              img2: require("@/assets/book_1.png"),
              date: "15 Octubre 2020",
              isBlur: false,
              isBook: "isBook1"
            },
            book2:{
              title: "Leo y Robert2",
              img: require("@/assets/book_2.jpg"),
              date: "12 noviembre 2020",
              isBlur: false,
              isBook: "isBook2"
            },
            book3:{
              title: "Leo y Robert3",
              img: require("@/assets/book_3.jpg"),
              date: "17 diciembre 2020",
              isBlur: false,
              isBook: "isBook3"
            },
          },
          dialogWindow:{
            title: "",
            img: "",
            description: "",
            links:{
              goodreads:"",
              kobo:"",
              amazon:"",
              apple:"",
              play:"",
              casa:"",
            }
          },
          icons:{
             twitter:{
                 img: require("@/assets/twitter.svg"),
                 name: "Twitter",
                 url:   "https://twitter.com/reginah_george"
             },
             facebook:{
                 img: require("@/assets/facebook.svg"),
                 name: "Facebook ",
                 url:   "https://www.facebook.com/LeoyRobert"
             },
             instagram:{
                 img: require("@/assets/instagram.svg"),
                 name: "Instagram",
                 url:   "https://instagram.com/reginah.george"
             },
             goodreads:{
                 img: require("@/assets/goodreads.svg"),
                 name: "Goodreads",
                 url:   "https://www.goodreads.com/author/show/20691207.Reginah_George"
             },
             email:{
                 img: require("@/assets/email.svg"),
                 name: "email",
                 url:   "mailto:leoyrobertsaga@gmail.com"
             }
         },
          dialog:{
            book1:{
              title: "#1 - Leo y Robert (11:50)",
              description: '<br> Leo Walden está a punto de terminar lo que ha sido uno de los peores años de su (corta) vida: su padre se ha marchado de casa, aún no ha superado su anterior relación y se ha quedado a las puertas de obtener una beca que podría haberle ayudado a olvidar todo. <br><br>Pero la vida de Leo cambia cuando Scorpion, una de las editoriales más prestigiosas del mundo, le contrata para ayudar a sacar adelante una importante campaña de marketing. Sin embargo, lo último que se espera es reencontrarse allí con Roberto Real. Porque por mucho que su nuevo supervisor no parezca recordarle, Leo sabe que Robert es aquel chico que conoció este pasado verano y terminó «evaporándose en mitad de la noche».<br><br>Porque... ¿es él, verdad? ¿O en verdad se trata de un completo desconocido?<br><br>Una novela sobre el amor y sus tipos, las casualidades y aprender a cerrar heridas abiertas para seguir adelante. <br><br> **Leo (11:50): ¿Te acuerdas de mí?** <br> **Robert (11:50): Lo recuerdo todo.**',
              img: require("@/assets/book_1.jpg"),
              img2: require("@/assets/book_1.png"),
              date: "8 Septiembre 2020",
              links:{
                goodreads:"https://www.goodreads.com/book/show/55307507-leo-y-robert-11",
                kobo:"https://www.kobo.com/es/es/ebook/leo-y-robert-11-50-libro-1-leo-y-robert-1",
                amazon:"https://www.amazon.es/dp/B08HW12Q1Q/?ref=exp_theboyinneon_dp_vv_d",
                apple:"https://books.apple.com/es/book/leo-y-robert-11-50-libro-1-leo-y-robert-1/id1531527466",
                play:"https://play.google.com/store/books/details/Reginah_George_Leo_y_Robert_11_50_Libro_1_Leo_y_Ro?id=IXX8DwAAQBAJ",
                casa:"https://www.casadellibro.com/ebook-leo-y-robert-1150-libro-1-leo-y-robert-1-ebook/9788417931308/11761876"
              }
            },
            book2:{
              title: "#2 - Leo y Robert: Antes de tiempo",
              description: '<br>«Dos chicos, Barcelona y un verano que lo cambió todo.»  <br><br> Tres relatos de la saga «Leo y Robert»<br><br> Relato I - Un café con sal: «Tengo que hablar contigo de algo importante». Leo, tan ingenuo y lleno de esperanzas como siempre, acude a la cita de Bruno en aquel café de la Gran Vía. No están en su mejor momento, vale, pero seguro que hay alguna forma de arreglarlo. Así funciona su... ¿relación? Bueno, ese lazo que los mantiene unidos desde hace años y con el que Leo se conforma. Aunque a veces tire demasiado. Aunque se haya enterado que él no es el único... Con tener un espacio en el corazón de Bruno le es suficiente. <br><br> Relato II - Un truco de magia: «No sé si la magia existe, pero hay ideas que son imposibles de quitarse de la cabeza». Un año antes de que Leo llegase a la oficina, Scorpion celebró una vez más su famosísima fiesta de Navidad, donde Elisa y Violeta fueron las elegidas para participar en un asombroso número de magia. ¿Queréis saber qué fue lo que ocurrió? <br><br> Relato III - Villa Plutón: ¿Sabíais que en Villa Plutón el verano y la música pueden cambiarlo todo? Después de dejarse convencer por Ares, Leo y un grupo de amigos de la universidad acudirán a un nuevo festival de música en Barcelona para ver en directo a Pink Tokyo, una de sus bandas favoritas. Allí, rodeado de miles de desconocidos ajenos a las preocupaciones, Leo se encontrará con Robert por primera vez en el tiempo.',
              img: require("@/assets/book_3.jpg"),
              img2: require("@/assets/book_2.png"),
              date: "8 Septiembre 2020",
              links:{
                goodreads:"https://www.goodreads.com/book/show/55366726-leo-y-robert-antes-de-tiempo",
                kobo:"https://www.kobo.com/es/es/ebook/leo-y-robert-antes-de-tiempo-libro-2-leo-y-robert-2",
                amazon:"https://www.amazon.es/dp/B08J8K267G/?ref=exp_theboyinneon_dp_vv_d",
                apple:"https://books.apple.com/es/book/leo-y-robert-antes-de-tiempo-libro-2-leo-y-robert-2/id1532126017",
                play:"https://play.google.com/store/books/details/Reginah_George_Leo_y_Robert_Antes_de_tiempo_Libro?id=xmP9DwAAQBAJ",
                casa:"https://www.casadellibro.com/ebook-leo-y-robert-antes-de-tiempo-libro-2-leo-y-robert-2-ebook/9788417931315/11772733"
              }
            },
            book3:{
              title: "#3 - Leo y Robert (00:00)",
              description: '<br> Un año después del sombrío desenlace de 11:50, Leo regresa a España tras su estancia en Inglaterra junto a Tom, un galán inglés con quien ha decidido mudarse de nuevo a Madrid por un gran motivo: ¡Leo va a publicar su primer libro! Pero hay un problema, y es que Kate, su agente literaria, le ha vendido los derechos de publicación a... Ediciones Scorpion. Y por supuesto, ni ella (ni el mismo Tom) tienen ni idea de qué fue lo que ocurrió exactamente cuando Leo «se marchó» de la editorial. <br><br> Robert, por su parte, ahora tiene un nuevo trabajo en una librería del centro y está tratando de reconducir su vida. Pero encontrarse a uno mismo es complicado, y a veces la soledad le empuja a buscar afecto en cuerpos que solo pasan por su habitación con otras intenciones. <br><br> Sin embargo, en una tarde de tormenta y por diferentes circunstancias, Leo termina refugiándose en la librería de Robert. Parece como si el tiempo hubiese decidido juntarlos una última vez, pero... ¿no es un poco tarde para ambos? <br><br>Robert (13:22): ¿Podemos vernos de nuevo? <br> Leo (21:31): Hoy, a medianoche.',
              img: require("@/assets/book_3.jpg"),
              img2: require("@/assets/book_3.png"),
              date: "8 Septiembre 2020",
              links:{
                goodreads:"https://www.goodreads.com/book/show/55461004-leo-y-robert-00",
                kobo:"https://www.kobo.com/es/es/ebook/leo-y-robert-00-00-libro-3-leo-y-robert-3",
                amazon:"https://www.amazon.es/dp/B08JF6QB2C/?ref=exp_theboyinneon_dp_vv_d",
                apple:"https://books.apple.com/es/book/leo-y-robert-00-00-libro-3-leo-y-robert-3/id1532302148",
                play:"https://www.amazon.es/dp/B08JF6QB2C/?ref=exp_theboyinneon_dp_vv_d",
                casa:"https://www.casadellibro.com/ebook-leo-y-robert-0000-libro-3-leo-y-robert-3-ebook/9788417931322/11772706"
              }
            }
          } 
      }    

    },
    
    components: {
      NavBar,
      VueMarkdown,
      // VModal
    },

    methods: {
        show(book) {
            this.$modal.show('book-dialog');
            let parent = this
            switch (book) {
              case "isBook1":
                parent.dialogWindow.title = parent.dialog.book1.title
                parent.dialogWindow.description = parent.dialog.book1.description
                parent.dialogWindow.img = parent.dialog.book1.img2
                parent.dialogWindow.links = parent.dialog.book1.links
                this[book] = true
                break;
              case "isBook2":
                this.isBook1= false
                parent.dialogWindow.title = parent.dialog.book2.title
                parent.dialogWindow.description = parent.dialog.book2.description
                parent.dialogWindow.img = parent.dialog.book2.img2
                parent.dialogWindow.links = parent.dialog.book2.links
                break;
              case "isBook3":
                this.isBook1= false
                parent.dialogWindow.title = parent.dialog.book3.title
                parent.dialogWindow.description = parent.dialog.book3.description
                parent.dialogWindow.img = parent.dialog.book3.img2
                parent.dialogWindow.links = parent.dialog.book3.links
                break;
            
              default:
                break;
            }
        },
        hide() {
          this.book1 = false
          this.book2 = false
          this.book3 = false
          this.$modal.hide('book-dialog');
        }
    },

    mounted(){

      let time = new Date().getHours()
      let parent = this
      // console.log(time);
      if (time > 6 && time <= 15) {
        document.documentElement.style.cssText = "--main-pink: #EE66A4";
        parent.mainBook = require("@/assets/book_1.png")
      } else if(time > 15 && time < 19){        
        document.documentElement.style.cssText = "--main-pink: #e2886b";
        parent.mainBook = require("@/assets/book_2.png")
      } else{        
        document.documentElement.style.cssText = "--main-pink: #383b5d";
        parent.mainBook = require("@/assets/book_3.png")
      }

      // console.log("hi");
    },

    mount () {
        this.show()
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
