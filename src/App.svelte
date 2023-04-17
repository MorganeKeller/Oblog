<script>
  import Router from "svelte-spa-router";

  import Header from "./lib/Header.svelte";
  import Footer from "./lib/Footer.svelte";

  import Error from "./lib/404.svelte";
  import Article from "./lib/Article.svelte";
  import ArticlesList from "./lib/ArticlesList.svelte";
  import Authors from "./lib/Authors.svelte";
  import CGU from "./lib/CGU.svelte";
  import Contact from "./lib/Contact.svelte";
  import Destinations from "./lib/Destinations.svelte";
  import Home from "./lib/Home.svelte";
  import Login from "./lib/Login.svelte";
  import Register from "./lib/Register.svelte";

  import Welcome from "./lib/Welcome.svelte";

  const routes = {
    "/": Welcome,
    "/home": Home,
    "/article": Article,
    "/destinations": Destinations,
    "/authors": Authors,
    "/articlesList": ArticlesList,
    "/contact": Contact,
    "/404": Error,
    "/cgu": CGU,
    "/login": Login,
    "/register": Register,
    "*": Error,
  };
</script>

<svelte:head>
  <title>Carnets de Voyages</title>
</svelte:head>

<Header />

<main>
  <Router {routes} />
</main>

<Footer />

<style>
</style>