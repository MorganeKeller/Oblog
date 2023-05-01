<script>
   import "../assets/scss/author.scss";
   import { link } from "svelte-spa-router";

   const getAuthors = async function () {
      const endpoint =
         import.meta.env.VITE_URL_DIRECTUS + "users";

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
         {#each articleAuthor as users}
            <div class="one-author">
               <h2>{users.user_name}</h2>

               <a use:link href="/authorArticles/{users.user_name}">Liste des articles</a>
            </div>
         {/each}
      </div>
   {/await}
</section>
