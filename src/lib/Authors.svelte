<script>
   import "../assets/scss/author.scss";
   import { link } from "svelte-spa-router";

   const getAuthors = async function () {
      const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";

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
      <p class="author-text">
         Ici vous trouverez tous nos contributeurs, qu'ils soient
         commentateurs ou rédacteurs. En cliquant sur chaque nom vous
         trouverez listés tous ses articles associés.
      </p>
      <div class="author-column">
    
         {#each articleAuthor as users}
            <div class="one-author">
               <a use:link href="/authorArticles/{users.id}"
                  ><h2>{users.user_name}</h2>
               </a>
            </div>
         {/each}
      </div>
   {/await}
</section>
