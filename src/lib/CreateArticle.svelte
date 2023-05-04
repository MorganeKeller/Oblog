<script>
    import "../assets/scss/createArticle.scss";
    import { link } from "svelte-spa-router";

    export let article_id;

    let article = [];

    let articleDestination = "";
    let articleTitle = "";
    let articleText = "";
    let articleDate = "";

    const handleSubmitForm = async (event) => {
        event.preventDefault();
        console.log(articleDestination, articleTitle, articleText, articleDate);

        //create a new article
        const new_article = await postArticle();
        //Adds a new article to the list in order to trigger Svelte's watcher
        //Regenerate the particle of DOM that depends on it
        article.push(new_article);
        //Refresh the article list officially
        article = [...article];

        //Empty the textarea
        articleDestination = "";
        articleText = "";
        articleDate = "";
        articleTitle = "";
    };

    //Function to retrieve article
    const getArticle = async (article) => {
        //In order to avoid an useless request, we return directly the list
        if (article.length !== 0) {
            return article;
        }

        let endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/article";

        //endpoint modification to filter on the article_id id only
        endpoint += "?filter=[article_id][_eq]=" + article_id;

        const response = await fetch(endpoint, {
            headers: {
                Authorization: "Bearer " + window.localStorage.getItem("token"),
            },
        });

        //Handling response errors
        if (response.ok === false) {
            //We trigger an error to enter the Svelte's catch
            throw new Error("Erreur de récupération des données");
        }

        const json = await response.json();

        //Extract error handling
        article = json.data;
        return json.data;
    };

    // Adding an article in BDD with the API
    const postArticle = async () => {
        const response = await fetch(
            import.meta.env.VITE_URL_DIRECTUS + "items/article/",
            {
                method: "POST",
                headers: {
                    "content-type": "application/json",
                    Authorization: "Bearer " + localStorage.getItem("token"),
                },
                body: JSON.stringify({
                    title: articleTitle,
                    content: articleText,
                    category_id: articleDestination,
                }),
            }
        );
        // Extract the token and return it
        const json = await response.json();
        return json.data;
    };
</script>

<section id="create-article">
    {#await getArticle}
        <p>Chargement en cours...</p>
    {:then article}
        <h1>Votre article</h1>
        <p>
            &#x27BD; Ici racontez nous vos périples, anecdotes, ce qui vous a
            émerveillé ou déçu, interpellé ou instruit...
        </p>

        <form
            on:submit={handleSubmitForm}
            class="create-form"
            action=""
            method="POST"
        >
            <div class="input-create">
                <label for="title">Titre de votre article</label>
                <input
                    type="text"
                    minlength="2"
                    maxlength="50"
                    required
                    bind:value={articleTitle}
                />
            </div>

            <div class="input-create">
                <label for="text" class="input-creat-textarea"
                    >Et pour nous partager votre aventure, c'est par là:</label
                >
                <textarea
                    required
                    minlength="30"
                    maxlength="800"
                    bind:value={articleText}
                />
            </div>

            <div class="input-create">
                <label for="continent-select"
                    >Choisissez une destination:
                </label>
                <select
                    name="destination"
                    id=""
                    required
                    bind:value={articleDestination}
                >
                    <option value="">----</option>
                    <option value="1">Afrique</option>/>
                    <option value="2">Europe</option>/>
                    <option value="3">Amérique</option>/>
                    <option value="4">Asie</option>/>
                    <option value="5">Océanie</option>/>
                </select>
            </div>

            <input type="submit" value="Envoyer" class="input-create-submit" />
        </form>
        <a use:link href="/login">Connectez-vous pour poster votre article</a>
    {/await}
</section>

<style>
</style>
