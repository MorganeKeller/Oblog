<script>
    import { link } from "svelte-spa-router";
    import mont_fuji from '../assets/img/Mont_Fuji.jpg';
    import new_zealand from '../assets/img/new_zealand.jpg';
    import grand_canyon from '../assets/img/grand_canyon.jpg';
    

    import home from '../assets/scss/home.scss';

   

    const getArticles = async () => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/Article";
        const response = await fetch(endpoint)
        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction

    return json.data;
}
console.log (getArticles);
</script>

    
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

        <img src={import.meta.env.VITE_URL_DIRECTUS + 'assets/' + article.pictures + '?key=medium'} alt="Mont Fuji">

            <p>{article.content}</p>

            <a use:link href="/article">Lire la suite</a>

    <p><strong>{article.author}</strong></p>
    <time datetime="2011-11-18T14:54:39">{article.created_at}</time>

</article>

{/each}

{/await}
</section>
<!-- <article >

        <h2>La nouvelle Zélande</h2>
        
        

        <img src={new_zealand} alt="paysage de Nouvelle-Zélande">

        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Incidunt saepe iste quasi quas fuga libero culpa voluptate doloremque, officia doloribus facilis ipsa ad odit ducimus, quaerat delectus deserunt aperiam commodi.</p>

        <a use:link href="/article">Lire la suite</a>

        <p><strong>MK</strong></p>
        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>

    </article>

    <article >

        <h2>Les Etats-Unis</h2>
        
        

        <img src={grand_canyon} alt="vue sur le Grand Canyon">

        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Incidunt saepe iste quasi quas fuga libero culpa voluptate doloremque, officia doloribus facilis ipsa ad odit ducimus, quaerat delectus deserunt aperiam commodi.</p>

        <a use:link href="/article">Lire la suite</a>

        <p><strong>QP</strong></p>
        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>

    </article> -->





<style>

</style>
