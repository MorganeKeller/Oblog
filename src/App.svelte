<script>
  import Header from "./lib/Header.svelte";
  import Router from "svelte-spa-router";
  import Footer from "./lib/Footer.svelte";

  import Home from "./lib/Home.svelte";
  import Article from "./lib/Article.svelte";
  import ArticlesList from "./lib/ArticlesList.svelte";
  import Destinations from "./lib/Destinations.svelte";
  import Authors from "./lib/Authors.svelte";
  import Login from "./lib/Login.svelte";
  import Contact from "./lib/Contact.svelte";
  import CGU from "./lib/CGU.svelte";
  import Register from "./lib/Register.svelte";
  import Error from "./lib/404.svelte";
  import CreateArticle from "./lib/CreateArticle.svelte";
  import CategoryArticles from "./lib/CategoryArticles.svelte";


  import Welcome from "./lib/Welcome.svelte";

  const routes = {
    "/": Welcome,
    "/home": Home,
    "/article/:id": Article,
    "/destinations": Destinations,
    "/authors": Authors,
    "/articlesList": ArticlesList,
    "/contact": Contact,
    "/404": Error,
    "/cgu": CGU,
    "/login": Login,
    "/register": Register,
    "/createArticle": CreateArticle,
    "/category/:categoryId": CategoryArticles,
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
