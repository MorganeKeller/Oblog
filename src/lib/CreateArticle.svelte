<script>
    import "../assets/scss/createArticle.scss";

    function goBack() {
        window.history.back();
    }
</script>

<section id="create-article">
    <h1>Votre article</h1>
    <p>
        &#x27BD; Ici racontez nous vos périples, anecdotes, ce qui vous a
        émerveillé ou déçu, interpellé ou instruit...
    </p>

    <form
        class="create-form"
        action=""
        method="POST"
        aria-label="Formulaire de création d'article"
    >
        <div class="input-create">
            <label for="pseudo">Votre pseudo</label>
            <input
                type="text"
                name="Nom"
                placeholder="ex: Newton23"
                required
                aria-label="Veuillez saisir votre pseudo"
            />
        </div>
        <div class="input-create">
            <label for="date">Date de rédaction</label>
            <input
                type="date"
                required
                aria-label="Veuillez renseigner la date de rédaction"
            />
        </div>
        <div class="input-create">
            <label for="title">Titre de votre article</label>
            <input
                type="text"
                minlength="2"
                maxlength="50"
                required
                aria-label="Saisissez un titre pour votre article"
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
                aria-label="Saisissez l'entiereté de votre article"
            />
        </div>
        <div class="input-create">
            <label for="continent-select">Choisissez une destination: </label>
            <select name="destination" id="" required>
                <optgroup label="Destination">
                    <option value="">----</option>
                    <option value="Afrique">Afrique</option>/>
                    <option value="Amérique">Amérique</option>/>
                    <option value="Asie">Asie</option>/>
                    <option value="Europe">Europe</option>/>
                    <option value="Océanie">Océanie</option>/>
                </optgroup>
            </select>
        </div>
        <div class="input-create">
            <label for="photo"
                >Si l'envie vous prend de nous partagez une de vos photos, c'est
                par ici:</label
            >
            <input
                type="file"
                accept="image/png, image/jpg, image/jpeg"
                aria-label="Ajoutez une photo au format jpeg, png ou jpg"
            />
        </div>
        <input
            type="submit"
            value="Envoyer"
            class="input-create-submit"
            aria-label="Valider l'envoi"
        />
    </form>
    <button on:click={goBack}>Retour</button>
</section>

<style>
</style>
