<script>
  import Router from "svelte-spa-router";
  import Header from "./lib/Header.svelte";
  import Footer from "./lib/Footer.svelte";
  import ArticlesList from "./lib/ArticlesList.svelte";
  import Authors from "./lib/Authors.svelte";
  import CGU from "./lib/CGU.svelte";
  import Contact from "./lib/Contact.svelte";
  import Home from "./lib/Home.svelte";
  

  const routes = {
    '/': Home,
    '/contact': Contact,
    '/articleslist': ArticlesList,
    '/authors' : Authors,
    '/cgu' : CGU, 
  }



</script>

<main>
  <Header />

  

  <Router
  {routes}/>
  
  

  <Footer />
</main>

<style>
</style>
