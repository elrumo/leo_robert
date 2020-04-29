<template>
    <div class="navbar-wrapper">
        <div class="navbar">
            <div class="navbar-mobile">
                <h5 class="navbar-el" v-for="nav in navBar" :key="nav.name"> 
                    <a :href="'/#' + nav.url">
                        {{ nav.name }}
                    </a>
                </h5>
            </div>
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
             nav2:{
                 name:"Libros",
                 url: "libros"
             }
         }
        }
    },

}
</script>

<style>
</style>