<!-- 
<script>
    import Login from "./Login.svelte";

    let comments = [];

    let commentText = "";
    let commentAuthor = "";
    let commentDate = "";
    //let CommentUpdate = "";

    const handleSubmitForm = async (event) => {
        event.preventDefault();
        console.log(commentText, commentAuthor, commentDate);

        const new_comment = await postComment();
        comments.push(new_comment);
        comments = [...comments];

        commentText = "";
        commentAuthor = "";
        commentDate = "";
    };

    const getComments = async (comments) => {
        if (comments.length !== 0) {
            return comments;
        }
        //POST http://chara-redif.vpnuser.lan:8055/items/commentary
        let endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/commentary";
        endpoint += "?filter[article_id][_eq]=" + article_id;

        const response = await fetch(endpoint, {
            headers: {
                Authorization: "Bearer " + window.localStorage.getItem("token"),
            },
        });

        if (response.ok === false) {
            throw new Error("Erreur de récupération des commentaires");
        }

        const json = await response.json();
        comments = json.data;
        return json.data;
    };

    // Ajout d'un commentaire en BDD avec l'api
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
                    article_id: article_id,
                }),
            }
        );
        // Extrait le token et le retourne
        const json = await response.json();
        return json.data;
    };
</script>

<section class="comments" aria-labelledby="comments-title">

<h2>Commentaires</h2>
{#await getComments(comments)}
<p>chargement en cours...</p>
{:then comments} 
{#each comments as comment}

<div aria-labelledby="comment-{comment.id}">
    <h3 id="comment-{comment.id}">{comment.text}</h3>
    <i>Posté le <time datetime="{comment.created_at}">{comment.created_at}</time></i>
    <p>{comment.text}</p>
</div>
{/each}

<form on:submit={handleSubmitForm} aria-labelledby="form-title">
    <h3 id="form-title">Votre commentaire</h3>
    <label for="author">Auteur</label>
    <input type="text" bind:value={commentAuthor}>
    
    <label for="date">Date</label>
    <input type="datetime" bind:value={commentDate} />
    
    
    <label for="Commentary">Commentaire</label>
    <input bind:value={commentText} type="text" name="Nom" placeholder="Votre nom" />
 
    <input type="submit" />
</form>
{:catch error}
<p>Connectez-vous pour voir les commentaires</p>
<Login reload=true/>
{/await}

</section>
<style>
</style> -->