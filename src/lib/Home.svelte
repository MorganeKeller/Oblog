<script>
    import { link } from "svelte-spa-router";
    import "../assets/scss/home.scss";

    export let params = {};

    // Extrait l'id issue de la route
    let article_id = params.id;

    const getArticles = async () => {
        // ?fields=*&sort=created_at&limit=3"
        const endpoint =
            import.meta.env.VITE_URL_DIRECTUS +
            "items/article?fields=*&limit=3&sort=-created_at";
        const response = await fetch(endpoint);

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction
        return json.data;
    };
</script>

<section class="home-background">
    <h1>Bienvenue dans nos Carnets de Voyages!</h1>

    <p>
        Vous voici arrivés à destination: ici découvrez les derniers articles
        publiés
    </p>

    <!-- Appel de la fonciton pour récupérer les données -->
    {#await getArticles()}
        <p>Chargement en cours...</p>

        <!-- Des que les données sont prêtes, je les range dans la variable articles -->
    {:then articles}
        {#each articles as article}
            <article class="home-article">
                <h2>{article.title}</h2>
                <!-- http://chara-redif.vpnuser.lan/directus/uploads/ -->
                <div class="article-bloc">
                    <a use:link href="/article/{article.id}"
                        ><img
                            src={"http://chara-redif.vpnuser.lan/directus/uploads/" +
                                article.pictures +
                                ".jpg"}
                            alt="illustration"
                        /></a
                    >
                    <!-- import.meta.env.UPLOAD_DIRECTUS  -->

                    <p class="overflow">{article.content}</p>
                </div>
                <div class="home-writer-date">
                    <p><strong>{article.author}</strong></p>
                    <time datetime={article.created_at}
                        >{new Date(article.created_at).toLocaleDateString(
                            "fr-FR"
                        )}</time
                    >
                </div>
                <a use:link href="/article/{article.id}">Lire la suite...</a>
            </article>
        {/each}
    {/await}
</section>

<style>
</style>
