<script>
  // Importer la fonction "push" du routeur Svelte SPA pour la navigation programmatique
  import { push } from "svelte-spa-router";
  // Importer le fichier de style destination.scss
  import "../assets/scss/destination.scss";

  // Fonction pour rediriger vers la page d'articles filtrés en fonction de l'ID de la catégorie
  const redirectToFilteredArticles = (category_id) => {
    push(`/category/${category_id}`);
  };
</script>

<!-- Structure HTML de la section des destinations -->
<section class="destinationsimg">
  <h1>Destinations</h1>
  <div class="destinations">
    <!-- Utiliser la fonction redirectToFilteredArticles avec l'ID de la catégorie correspondante -->
    <a role="menuitem" on:click={() => redirectToFilteredArticles(1)}
      ><span>&#x27BD;</span>Afrique</a
    >
    <a role="menuitem" on:click={() => redirectToFilteredArticles(2)}
      ><span>&#x27BD;</span>Europe</a
    >
    <a role="menuitem" on:click={() => redirectToFilteredArticles(3)}
      ><span>&#x27BD;</span>Amerique</a
    >
    <a role="menuitem" on:click={() => redirectToFilteredArticles(4)}
      ><span>&#x27BD;</span>Asie</a
    >
    <a role="menuitem" on:click={() => redirectToFilteredArticles(5)}
      ><span>&#x27BD;</span>Océanie</a
    >
  </div>
</section>
