<script>
            import { link } from "svelte-spa-router";

</script>

<section class="main-register">
    <h1>Création de compte</h1>
    <div class="before-register">
        <p>
            Avant de te créer un compte on souhaiterait que tu jettes un oeil à
            nos <a use:link href="/cgu">&#x27BD; Conditions Générales</a>
        </p>
    </div>
    <form action="#" aria-label="Informations d'enregistrement">
        <div class="register-form">
            <label for="name">Nom</label>
            <input required name="name" placeholder="ex : NEWTON" />
            <label for="firstname">Prénom</label>
            <input required name="firstname" placeholder="ex : Isaac" />
            <label for="pseudo">Pseudo</label>
            <input required name="pseudo" placeholder="ex=Isaacnewton23" />

            <label for="email">Email</label>
            <input
                required
                type="email"
                name="email"
                placeholder="ex : i.newton@test.fr"
            />

            <label for="password">Mot de passe</label>
            <input
                required
                type="password"
                name="password"
                placeholder="***********"
            />
        </div>
        <div class="register-validation">
            <input type="submit" value="&#x27BD; Créer un compte" />
        </div>
    </form>
</section>
