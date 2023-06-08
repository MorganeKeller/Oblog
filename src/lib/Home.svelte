<script>
    import { link } from "svelte-spa-router";
    import "../assets/scss/home.scss";

    var tabAuthor = [];

    const getArticles = async () => {
       
        const endpoint =
            import.meta.env.VITE_URL_DIRECTUS +
            "items/article?fields=*&limit=3&sort=-created_at";
        const response = await fetch(endpoint);

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction
        return json.data;
    };

    //Get Users by nicknames
    const getAuthors = async function () {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";

        const response = await fetch(endpoint);

        const json = await response.json();
        let authors1 = json.data;
        for (var index in authors1) {
            tabAuthor[authors1[index].id] = authors1[index].user_name;
        }
        return json.data;
    };
    getAuthors();
</script>

<section class="home-background">
    <h1>🟇 Bienvenue! 🟇</h1>
    <p class="presentation">
        Bienvenue dans nos Carnet de voyages! Que ce soit pour des échanges ou simplement pour découvrir de nouvelles cultures, ici, nous comptons partager nos aventures, nos découvertes et nos expériences dans les endroits les plus incroyables du monde, qu'ils soient près ou loin de chez vous par le biais de petits articles. Ce blog à pour but d'être collaboratif, n'hésitez donc pas à vous inscrire pour commenter et participer en partageant également vos souvenirs.<br> <strong>N'oubliez pas de profiter du voyage!</strong></p>

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
                <div class="article-bloc">
                    <a use:link href="/article/{article.id}">
                        <img src={import.meta.env.VITE_URL_DIRECTUS +
                                "assets/" +
                                article.pictures}
                            aria-hidden="true"
                            alt="illustration"/></a>
                </div>
                <h2>{article.title}</h2>
                <div class="home-writer-date">
                    <strong>{tabAuthor[article.author]}</strong>
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
