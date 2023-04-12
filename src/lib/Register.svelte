<script></script>

<main>
    <h1>Création de compte</h1>
    <div>
        <p>
            Avant de te créer un compte on souhaiterait que tu jettes un oeil à
            nos Conditions Générales
        </p>
        <a href=""><button>Nos CGU</button></a>

        <form action="#" aria-label="Informations d'enregistrement">
            <div>
                <label for="name">Nom</label>
                <label for="firstname">Prénom</label>
                <label for="pseudo">Pseudo</label>
                <input required name="name" placeholder="ex : NEWTON" />
                <input required name="firstname" placeholder="ex : Isaac" />
                <input required name="pseudo" placeholder="ex=Isaacnewton54" />
            </div>

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

            <div>
                <input type="submit" value="Créer un compte" />
            </div>
        </form>
    </div>
</main>
