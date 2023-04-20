<script>
    import cgu from "../assets/scss/comments.scss";
    import { link } from "svelte-spa-router";

    let commentary = [];

    //Form informations
    let commentText = "très beau pays";
    let commentAuthor = "Gilou";
    let commentDate = "12/05/22";
    //let CommentUpdate = "";

    const handleSubmitForm = async (event) => {
        event.preventDefault();
        console.log(commentText, commentAuthor, commentDate);

        //create a new comment
        const new_comment = await postComment();
        //Adds a new comment to the list in order to trigger Svelte's watcher
        //Regenerate the part of DOM that depends on it
        commentary.push(new_comment);
        //Refresh the commentary list officially
        commentary = [...commentary];

        //Empty the textarea
        commentText = "";
        commentAuthor = "";
        commentDate = "";
    };

    //Function to retrieve comments
    const getComments = async (commentary) => {
        //In order to avoid an useless request, we return directly the list
        if (commentary.length !== 0) {
            return commentary;
        }

        let endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/commentary";

        //endpoint modification to filter on the article id only
        endpoint += "?filter=[article_id][_eq]=" + "article_id";

        const response = await fetch(endpoint, {
            headers: {
                Authorization: "Bearer " + window.localStorage.getItem("token"),
            },
        });

        //Handling response errors
        if (response.ok === false) {
            //We trigger an error to enter the Svelte's catch
            throw new Error("Erreur de récupération des commentaires");
        }

        const json = await response.json();

        //Extract error handling
        commentary = json.data;
        return json.data;
    };

    // Adding a comment in BDD with the API
    const postComment = async () => {
        const response = await fetch(
            import.meta.env.VITE_URL_DIRECTUS + "items/commentary",
            {
                method: "POST",
                headers: {
                    "content-type": "application/json",
                    Authorization: "Bearer " + localStorage.getItem("token"),
                },
                body: JSON.stringify({
                    text: commentText,
                    author: commentAuthor,
                    date: commentDate,
                }),
            }
        );
        // Extract the token and return it
        const json = await response.json();
        return json.data;
    };
</script>

<section class="comments" aria-labelledby="comments-title">
    <h2>Commentaires</h2>
    <!-- Function calling -->
    {#await getComments(commentary)}
        <p>chargement en cours...</p>
        <!-- Once the promise is kept, we store the function's result in the variable "comments" -->
    {:then comments}
        <!-- Go through the whole list of comments, and for each element we store it in the variable "comment" -->
        {#each comments as commentary}
            <div aria-labelledby="comment-{commentary.id}">
                <h3 id="comment-{commentary.id}">{commentary.text}</h3>
                <i
                    >Posté le <time datetime={commentary.created_at}
                        >{commentary.created_at}</time
                    ></i
                >
                <p>{commentary.text}</p>
            </div>
        {/each}

        <form
            on:submit={handleSubmitForm}
            aria-labelledby="form-title"
            class="comments-form"
        >
            <h3 id="form-title">Votre commentaire</h3>
            <label for="author">Auteur</label>
            <input type="text" bind:value={commentAuthor} />

            <label for="date">Date</label>
            <input type="datetime" bind:value={commentDate} />

            <label for="Commentary">Commentaire</label>
            <input
                bind:value={commentText}
                type="text"
                name="Nom"
                placeholder="Votre nom"
            />

            <input type="submit" />
        </form>
    {:catch error}
        <a use:link href="/login">Connectez-vous pour commenter</a>
    {/await}
</section>

<style>
</style>
