<script>
  import Header from "./lib/Header.svelte";
  import Footer from "./lib/Footer.svelte";
  import ArticlesList from "./lib/ArticlesList.svelte";
  import Authors from "./lib/Authors.svelte";
  import CGU from "./lib/CGU.svelte";
  import Contact from "./lib/Contact.svelte";
  import Home from "./lib/Home.svelte";
  import Router from "svelte-spa-router";

  const router = {
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
  {router}/>
  
  

  <Footer />
</main>

<style>
</style>
