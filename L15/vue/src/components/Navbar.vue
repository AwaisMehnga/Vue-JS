<template>
    <div class="navbar">
        <a 
            v-for="(page, index) in pages" 
            target="_blank"
            :href="page.link.url" 
            :key="index"
        >{{page.link.text}}</a>
        <div @click="showNav=!showNav" class="navbar-burger"><span>&#9776;</span></div>
        <div class="navbar-responsive" :class="{dispNav: showNav==true, hideNav:showNav==false}">
            <a 
                v-for="(page, index) in pages" 
                target="_blank"
                :href="page.link.url" 
                :key="index"
            >{{page.link.text}}</a>
        </div>
    </div>
</template>

<script>
    export default{
        props:['pages','activePage','showNav','setActivePage']
    }
</script>
