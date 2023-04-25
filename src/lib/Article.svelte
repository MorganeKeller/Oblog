<script>
    import "../assets/scss/article.scss";
    import Comments from "../lib/Comments.svelte";

    export let params = {};

    // Extrait l'id issue de la route
    let article_id = params.id;

    const getPublication = async () => {
        // ?fields=*.*.*&sort=created_at&limit=3"
        const endpoint =
            import.meta.env.VITE_URL_DIRECTUS + "items/article/" + article_id;
        const response = await fetch(endpoint);
        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction
        return json.data;
    };

    function goBack() {
        window.history.back();
    }
</script>

<article class="art">
    {#await getPublication()}
        <!-- <h1>Le Japon</h1> -->
    {:then publication}
        <h2>{publication.title}</h2>
        <p>
            {publication.content}
        </p>
        <img
            src={"http://chara-redif.vpnuser.lan/directus/uploads/" +
                publication.pictures +
                ".jpg"}
            alt=""
        />

        <div class="author_date">
            <p>
                Par: <b>{publication.author}</b>
                Le:
                <b
                    ><time datetime={publication.created_at}
                        >{new Date(publication.created_at).toLocaleDateString(
                            "fr-FR"
                        )}</time
                    ></b
                >
            </p>
            <button on:click={goBack}>Retour</button>
        </div>
    {/await}
    <Comments {article_id} />
</article>

<style>
</style>
