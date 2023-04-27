<script>
    import { link } from "svelte-spa-router";
    import mont_fuji from '../assets/img/Mont_Fuji.jpg';
    import new_zealand from '../assets/img/new_zealand.jpg';
    import grand_canyon from '../assets/img/grand_canyon.jpg';
    

    import '../assets/scss/home.scss';

    export let params = {};
    console.log(params)

    // Extrait l'id issue de la route
    let article_id = params.id;

        const getArticles = async () => {
            // ?fields=*&sort=created_at&limit=3"
            const endpoint = import.meta.env.VITE_URL_DIRECTUS + 'items/article?fields=*&limit=3&sort=created_at';
            const response = await fetch(endpoint);
           
            // Gestion des erreurs de réponse

            const json = await response.json();

            // Gestion des erreurs d'extraction
console.log(json);
        return json.data;

    }
    console.log (getArticles);

   
</script>

<form action="#">
    <select name="Tri" id="">
      <option value="">Auteur</option>
      <option value="">Date</option>

    </select>
    <input type="submit" value="Submit" />
</form>
   
    <section class="home-background">

        <h1>Bienvenue dans nos Carnets de Voyages!</h1>

            <p class="text-center">
            Vous voici arrivés à destination: ici découvrez les derniers articles
            publiés
            </p>

<!-- Appel de la fonciton pour récupérer les données -->
    {#await getArticles()}
        <p>ça charge...</p>

    <!-- Des que les données sont prêtes, je les range dans la variable articles -->
   {:then articles} 


{#each articles as article}
<article >

    <h2>{article.title}</h2>
    <!-- http://chara-redif.vpnuser.lan/directus/uploads/ -->
        <img src={ 'http://chara-redif.vpnuser.lan/directus/uploads/' + article.pictures + '.jpg'} alt="illustration">
        <!-- import.meta.env.UPLOAD_DIRECTUS  -->

            
            <p class="overflow">{article.content}</p>

            <a use:link href="/article/{article.id}">Lire la suite</a>

    <p><strong>{article.author}</strong></p>
    <time datetime="2011-11-18T14:54:39">{article.created_at}</time>

</article>

{/each}

{/await}
</section>

<style>

</style>
