<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/destination.scss";

  // Fonction pour rediriger vers la page d'articles filtrés en fonction de l'ID de la catégorie
  const redirectToFilteredArticles = (category_id) => {
    link(`/category/${category_id}`);
  };
</script>

<section class="destinationsimg">
  <h1>Destinations</h1>
  <div class="destinations">
    <!-- Utiliser la fonction redirectToFilteredArticles avec l'ID de la catégorie correspondante -->
    <a role="menuitem" on:click={() => redirectToFilteredArticles(1)}>Afrique</a>
    <a role="menuitem" on:click={() => redirectToFilteredArticles(2)}>Europe</a>
    <a role="menuitem" on:click={() => redirectToFilteredArticles(3)}>Amérique</a>
    <a role="menuitem" on:click={() => redirectToFilteredArticles(4)}>Asie</a>
    <a role="menuitem" on:click={() => redirectToFilteredArticles(5)}>Océanie</a>
  </div>
</section>
