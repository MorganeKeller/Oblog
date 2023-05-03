<script>
  import { push } from "svelte-spa-router";
  import "../assets/scss/destination.scss";

  // Fonction pour rediriger vers la page d'articles filtrés en fonction de l'ID de la catégorie
  const redirectToFilteredArticles = (category_id) => {
    push(`/category/${category_id}`);
  };
</script>

<section class="destinationsimg">
  <h1>Destinations</h1>
  <div class="destinations">
    <!-- Utiliser la fonction redirectToFilteredArticles avec l'ID de la catégorie correspondante -->
    <button type="button" on:click={() => redirectToFilteredArticles(1)}>Afrique</button>
    <button type="button" on:click={() => redirectToFilteredArticles(2)}>Europe</button>
    <button type="button" on:click={() => redirectToFilteredArticles(3)}>Amérique</button>
    <button type="button" on:click={() => redirectToFilteredArticles(4)}>Asie</button>
    <button type="button" on:click={() => redirectToFilteredArticles(5)}>Océanie</button>
  </div>
</section>
