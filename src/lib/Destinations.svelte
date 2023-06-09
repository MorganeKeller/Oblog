<script>
  import { push } from "svelte-spa-router";
  import "../assets/scss/destination.scss";
  import LogoDirect from "../assets/img/direction.png";

  // Fonction pour rediriger vers la page d'articles filtrés en fonction de l'ID de la catégorie
  const redirectToFilteredArticles = (category_id) => {
    push(`/category/${category_id}`);
  };
</script>

<section class="destinationsimg">
  <h1>Destinations</h1>
  <img class="direction" src={LogoDirect} alt="panneau indicateur" />
  <p>Choisissez le continent où se situera votre prochaine escapade!</p>
  <div class="destinations">
    <!-- Utiliser la fonction redirectToFilteredArticles avec l'ID de la catégorie correspondante -->
    <button type="button" on:click={() => redirectToFilteredArticles(1)}
      ><span>⤖</span> Afrique</button
    >
    <button type="button" on:click={() => redirectToFilteredArticles(2)}>
      Europe <span>⭅</span></button
    >
    <button type="button" on:click={() => redirectToFilteredArticles(3)}
      ><span>&#x27BD;</span> Amérique</button
    >
    <button type="button" on:click={() => redirectToFilteredArticles(4)}>
      Asie<span>⬰</span></button
    >
    <button type="button" on:click={() => redirectToFilteredArticles(5)}
      ><span>⟴</span> Océanie</button
    >
  </div>
</section>
