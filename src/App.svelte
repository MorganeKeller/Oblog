<script>
  import Router from "svelte-spa-router";
  import Header from "./lib/Header.svelte";
  import Footer from "./lib/Footer.svelte";

  import Welcome from "./lib/Welcome.svelte";
  import Home from "./lib/Home.svelte";
  import Contact from "./lib/Contact.svelte";
  import Article from "./lib/Article.svelte";
  import ArticlesList from "./lib/ArticlesList.svelte";
  import Destinations from "./lib/Destinations.svelte";
  import Authors from "./lib/Authors.svelte";
  import AuthorArticles from "./lib/AuthorArticles.svelte";
  import Login from "./lib/Login.svelte";
  import CGU from "./lib/CGU.svelte";
  import Register from "./lib/Register.svelte";
  import Error from "./lib/404.svelte";
  import CreateArticle from "./lib/CreateArticle.svelte";
  import CategoryArticles from "./lib/CategoryArticles.svelte";



  const routes = {
    "/": Welcome,
    "/home": Home,
    "/contact": Contact,
    "/article/:id": Article,
    "/articlesList": ArticlesList,
    "/destinations": Destinations,
    "/authors": Authors,
    "/authorArticles/:id": AuthorArticles,
    "/login": Login,
    "/cgu": CGU,
    "/register": Register,
    "/404": Error,
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
