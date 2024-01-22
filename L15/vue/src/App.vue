<template>
  <Navbar 
    :pages="pages" 
    :show-nav="showNav" 
    :active-page="activePage"
    :set-active-page="(index)=>activePage=index"
  ></Navbar>
  <Page></Page>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Page from './components/page.vue';

export default {
  components: {
    Navbar,
    Page,
  },
  data() {
    return {
      showNav: false,
      activePage: 0,
      pages: [
        {
          link: { text: "Home", url: "index.html" },
          title: "Home",
        },
        {
          link: { text: "Github", url: "https://github.com/AwaisMehnga" },
          title: "Github",
        },
        {
          link: { text: "LinkedIn", url: "https://www.linkedin.com/in/awaismehnga/" },
          title: "LinkedIn",
        },
        {
          link: { text: "MealDB", url: "https://www.themealdb.com/" },
          title: "MealDB",
        },
      ],
      methods: {
        
      },
    };
  },
};
</script>
