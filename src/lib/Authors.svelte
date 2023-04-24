<script>
   import author from '../assets/scss/author.scss';
   import { link } from "svelte-spa-router";


   const getAuthors = async function () {
      const endpoint = import.meta.env.VITE_URL_DIRECTUS + 'items/user/';
      const response = await fetch (endpoint);

      const json= await response.json ();

      return json.data;
   }
   console.log(getAuthors);



</script>

<section class="authors">

   {#await getAuthors()}

   <p>chargement en cours...</p>
      
   {:then utilisateurs} 
      
   
   <h1>Les Auteurs</h1>
   {#each utilisateurs as auteur}
      
   
   <div class="one-author">
      <h2>{auteur.user_name}</h2>

      <a use:link href="/articlesList">Liste des articles</a>
      
   </div>
   

   {/each}
   {/await}
</section>