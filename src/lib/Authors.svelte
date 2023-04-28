<script>
   import "../assets/scss/author.scss";
   import { link } from "svelte-spa-router";

   const getAuthors = async function () {
      const endpoint =
         import.meta.env.VITE_URL_DIRECTUS + "items/article?fields=user_id";
      const response = await fetch(endpoint);

      const json = await response.json();

      return json.data;
   };
</script>

<section class="authors">
   {#await getAuthors()}
      <p>chargement en cours...</p>
   {:then articleAuthor}
      <h1>Les Auteurs</h1>
      <div class="author-column">
         {#each articleAuthor as article}
            <div class="one-author">
               <h2>{article.author}</h2>

               <a use:link href="/articlesList">Liste des articles</a>
            </div>
         {/each}
      </div>
   {/await}
</section>
