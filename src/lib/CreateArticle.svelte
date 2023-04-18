<script>
</script>

<section id="create-article">
    <h1>Votre article</h1>
    <p>
        &#x27BD; Ici racontez nous vos périples, anecdotes, ce qui vous a
        émerveillé ou déçu, interpellé ou instruit...
    </p>

    <form class="create-form" action="" method="POST">
        <div class="input-create">
            <label for="pseudo">Votre pseudo</label>
            <input type="text" name="Nom" placeholder="ex: Newton23" required />
        </div>
        <div class="input-create">
            <label for="date">Date de rédaction</label>
            <input type="date" required />
        </div>
        <div class="input-create">
            <label for="title">Titre de votre article</label>

            <input type="text" minlength="2" maxlength="30" />
        </div>
        <div class="input-create">
            <label for="text" class="input-creat-textarea"
                >Et pour nous partager votre aventure, c'est par là:</label
            >
            <textarea required />
        </div>
        <div class="input-create">
            <label for="continent-select">Choisissez une destination: </label>
            <select name="destination" id="" required>
                <option value="">----</option>
                <option value="Afrique">Afrique</option>/>
                <option value="Afrique">Amérique</option>/>
                <option value="Afrique">Asie</option>/>
                <option value="Afrique">Europe</option>/>
                <option value="Afrique">Océanie</option>/>
            </select>
        </div>
        <div class="input-create">
            <label for="photo"
                >Si l'envie vous prend de nous partagez une de vos photos, c'est
                par ici:</label
            >
            <input type="file" accept="image/png, image/jpg, imagejpeg" />
        </div>
        <input type="submit" value="Envoyer" class="input-create-submit" />
    </form>
</section>

<style>
</style>
