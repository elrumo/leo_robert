<template>
    <div class="navbar-wrapper">
        <div class="navbar">
            <div class="navbar-icons">
                <a v-for="icon in icons" :key="icon.name" target="_blank" class="nav-hover" :href="icon.url">
                    <img class="social-icon" :src="icon.img" alt="">
                </a>
            </div>

            <h5 class="navbar-el float-right nav-hover" v-for="nav in navBar" :key="nav.name"> 
                <a :href="'/#' + nav.url">
                    {{ nav.name }}
                </a>
            </h5>
        </div>
    </div>
</template>

<script>
export default {
    name: "Navbar",

    data(){
        return {
         navBar:{
             nav1:{
                 name:"Sobre la autora",
                 url: "autora"
             },
            //  nav2:{
            //      name:"Libros",
            //      url: "libros"
            //  }
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
        }
    },

}
</script>

<style>
</style>