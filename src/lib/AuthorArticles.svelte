<script>
    import { link } from "svelte-spa-router";
    import "../assets/scss/authorArticles.scss";

    // export const params = {};
    // let users_id = params.id;
    //export let users;
export let users;
let articles = [];
articles = [...articles]

    const getArticlesByAuthor = async () => {
        if (articles.length == 0) {
            return "Cet auteur n'a pas encore écrit d'article";
        }

        let endpoint =
            import.meta.env.VITE_URL_DIRECTUS +
            "items/article?fields=*&sort=users.user_name";
            // endpoint += "?filter[users.user_name][_eq]=" + users.user_name ;

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
                    <img
                        src={"http://chara-redif.vpnuser.lan/directus/uploads/" +
                            article.pictures +
                            ".jpg"}
                        alt="illustration"
                    />
                    <!-- import.meta.env.UPLOAD_DIRECTUS  -->

                    <p class="overflow">{article.content}</p>
                </div>
                <div class="home-writer-date">
                    <p><strong>{article.author}</strong></p>
                    <time datetime={article.created_at}
                        >{new Date(article.created_at).toLocaleDateString("fr-FR")}</time
                    >
                </div>
                <a use:link href="/article/{article.id}">Lire la suite...</a>
            </article>
        {/each}
    {/await}
</section>
