<script>
    import { link } from "svelte-spa-router";
    import "../assets/scss/home.scss";

    var tabAuthor = [];

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

    const getAuthors = async function () {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";

        const response = await fetch(endpoint);

        const json = await response.json();
        let authors1 = json.data;
        for (var index in authors1){
            tabAuthor[authors1[index].id]=authors1[index].user_name;
        }
        return json.data;
    };
    getAuthors();
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
                            src={import.meta.env.VITE_URL_DIRECTUS + "assets/"+
                                article.pictures 
                                }
                            aria-hidden=true alt="illustration"
                        /></a
                    >
                    <!-- import.meta.env.UPLOAD_DIRECTUS  -->

                    <p class="overflow">{article.content}</p>
                </div>
                <div class="home-writer-date">
                    <p><strong>{tabAuthor[article.author]}</strong></p>
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


