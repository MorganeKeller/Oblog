<script>
    import "../assets/scss/comments.scss";
    import { link } from "svelte-spa-router";

    let commentary = [];
    export let article_id;

    //Form informations
    let commentText = "";
    let commentAuthor = "";
    let commentDate = "";
    //let CommentUpdate = "";

    const handleSubmitForm = async (event) => {
        event.preventDefault();

        //create a new comment
        const new_commentary = await postComment();
        //Adds a new comment to the list in order to trigger Svelte's watcher
        //Regenerate the part of DOM that depends on it
        commentary.push(new_commentary);
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
        endpoint += "?filter[article_id][_eq]=" + article_id;

        const response = await fetch(endpoint, {
            headers: {
                Authorization: "Bearer " + window.localStorage.getItem("token"),
            },
        });
        //Handling response errors
        if (response.ok === false) {
            //We trigger an error to enter the Svelte's catch
            throw new Error("Erreur de récupération des commentaries");
        }

        const json = await response.json();

        //Extract error handling
        commentary = json.data;

        return json.data;
    };

    // Adding a comment in BDD with the API
    const postComment = async () => {
        const response = await fetch(
            import.meta.env.VITE_URL_DIRECTUS + "items/commentary/",
            {
                method: "POST",
                headers: {
                    "content-type": "application/json",
                    Authorization: "Bearer " + localStorage.getItem("token"),
                },
                body: JSON.stringify({
                    text: commentText,
                    article_id: article_id,
                    author: localStorage.getItem("id"),
                
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
            <i
                >Posté le: <b>{commentary.created_at}</b>
                Par: <b>{commentary.author}</b>
            </i>
            <div aria-labelledby="comment-{commentary.id}" class="div-comment">
                <p id="comment-{commentary.id}">{commentary.text}</p>
            </div>
        {/each}

        <form on:submit={handleSubmitForm} aria-labelledby="form-title">
            <h3 id="form-title">Votre commentaire</h3>
            <label for="Commentary"></label>
            <textarea
                required
                class="input-comment"
                bind:value={commentText}
                name="Nom"
                placeholder="Votre commentaire"
            />

            <input class="submit" type="submit" />
        </form>
    {:catch error}
        <a class="logToComment" use:link href="/login"
            >Connectez-vous pour commenter</a
        >
    {/await}
</section>

<style>
</style>
