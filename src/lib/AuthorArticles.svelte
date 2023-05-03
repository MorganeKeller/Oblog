<script>
    import { link } from "svelte-spa-router";
    import "../assets/scss/authorArticles.scss";

    export let params = {};
    var tabAuthor = [];

    const getAuthors = async function () {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";

        const response = await fetch(endpoint);

        const json = await response.json();
        let authors = json.data;
        for (var index in authors) {
            tabAuthor[authors[index].id] = authors[index].user_name;
        }
        return json.data;
    };
    getAuthors();

    const getArticlesByAuthor = async () => {
        const endpoint =
            import.meta.env.VITE_URL_DIRECTUS +
            "items/article?filter[author][_eq]=" +
            params.id;

        const response = await fetch(endpoint);

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction
        return json.data;
    };
</script>

<section class="AuthorArticle-background">
    <h1>Les articles</h1>

    <p>Voici tous les articles de l'auteur</p>
    {#await getArticlesByAuthor()}
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
                        src={import.meta.env.VITE_URL_DIRECTUS +
                            "assets/" +
                            article.pictures}
                        alt="illustration"
                    /></a>
                    <!-- import.meta.env.UPLOAD_DIRECTUS  -->

                    <p class="overflow">{article.content}</p>
                </div>
                <a use:link href="/article/{article.id}">Lire la suite...</a>
                <div class="home-writer-date">
                    <p><strong>{tabAuthor[article.author]}</strong></p>
                    <time datetime={article.created_at}
                        >{new Date(article.created_at).toLocaleDateString(
                            "fr-FR"
                        )}</time
                    >
                </div>
            </article>
        {/each}
    {/await}
</section>
