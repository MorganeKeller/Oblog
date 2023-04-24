<script>
    import akihabara from "../assets/img/Akihabara.jpg";
    import chateau from "../assets/img/chateau_oasaka.jpg";
    import mont_fuji from "../assets/img/Mont_Fuji.jpg";

    import article from "../assets/scss/article.scss";

<<<<<<< HEAD
    import Comments from "./Comments.svelte";
    // export let params = {};
    // let article_id = params.id;
=======
    export let params = {};
    console.log(params)

    // Extrait l'id issue de la route
    let article_id = params.id;

        const getPublication = async () => {
            // ?fields=*.*.*&sort=created_at&limit=3"
            const endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/article/" + article_id;
            const response = await fetch(endpoint);
            // Gestion des erreurs de réponse

            const json = await response.json();

            // Gestion des erreurs d'extraction
console.log(json);
        return json.data;

    }
    console.log (getPublication);

>>>>>>> home
</script>



<article class="art">

    {#await getPublication()}

    <h1>Le Japon</h1>
    
        
    {:then publication} 

    <h2>{publication.title}</h2>

    <p>
        {publication.content}
    </p>

    <img src={'http://chara-redif.vpnuser.lan/directus/uploads/' + publication.pictures + '.jpg'} alt=""/>

<<<<<<< HEAD
    <Comments />
=======
   {/await}
>>>>>>> home
</article>


<style>
</style>
