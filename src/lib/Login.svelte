<script>
    import { link } from "svelte-spa-router";
    import { push } from "svelte-spa-router";
    import "../assets/scss/login.scss";

    let email;
    let password;
    let error = "";

    // add a login variable
    let isLoggedIn = false; 

    //we retrieve user data
    const getME = async () => {
        const response = await fetch(
            import.meta.env.VITE_URL_DIRECTUS + "users/me",
            {
                method: "GET",
                headers: {
                    "content-type": "application/json",
                    Authorization: "Bearer " + localStorage.getItem("token"),
                },
            }
        ).then((data) => {
            return data;
        });
        
        // Extract the token and return it
        const json = await response.json();
        return json.data;
    };

    const handleSubmit = async (event) => {
        event.preventDefault();
        const token = await connect();

        //In case of good return we follow the following instructions
        if (token !== false) {
            // storage in "localstorage"
            window.localStorage.setItem("token", token);
            let me = getME();
            //    on récupère l'id qui provient du user/me (utilisateur connecté)
            me.then((value) => {
                window.localStorage.setItem("id", value.id);
            });
            // modification de l'état de connexion après connexion réussie
            isLoggedIn = true;
        }
    };

    const handleLogout = () => {
        // nettoyage du localStorage
        window.localStorage.removeItem("token");

        // modification de l'état de connexion après déconnexion réussie
        isLoggedIn = false;

        // retour à la page de connexion
        push("/login");
    };

    const connect = async () => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "auth/login";
        const response = await fetch(endpoint, {
            method: "POST",
            body: JSON.stringify({
                email: email,
                password: password,
            }),
            headers: {
                "Content-Type": "application/json",
            },
        });

        // response error handling
        if (response.ok !== true) {
            error = "Adresse e-mail ou mot de passe incorrect";
            return false;
        }

        const json = await response.json();
        // Extraction errors handling

        // Token recovery only
        return json.data.access_token;
    };

    // on vérifie l'état de connexion pour afficher le bouton de déconnexion
    const token = window.localStorage.getItem("token");
    if (token) {
        isLoggedIn = true;
    }
</script>

<div class="login-background">
    <h1>Connexion</h1>
    {#if isLoggedIn}
    <p>Bienvenue!<br>Vous êtes connecté(e) en tant que </p>
        <!-- on vérifie l'état de connexion pour afficher le bouton de déconnexion -->
        <button class="unlog" on:click={handleLogout}>Se déconnecter</button>
    {:else}
        <section class="section-form">
            <form
                on:submit={handleSubmit}
                action="#"
                aria-label="Informations de connexion"
            >
                <div class="input-login">
                    <label for="email">E-mail: </label>
                    <input
                        bind:value={email}
                        required
                        type="email"
                        name="email"
                        placeholder="ex : i.newton@test.fr"
                        aria-label="Renseignez votre e-mail"
                    />
                </div>

                <div class="input-login">
                    <label for="password">Mot de passe: </label>
                    <input
                        bind:value={password}
                        required
                        type="password"
                        name="password"
                        placeholder="***********"
                        aria-label="Renseignez votre mot de passe"
                    />
                </div>

                <input
                    class="connexion"
                    aria-label="Se connecter"
                    type="submit"
                    value=" &#x27BD; Se connecter"
                />
            </form>
            <div class="text-login-register">
                <h2>Pas encore de compte?</h2>
                <p>
                    Si l'envie te prend de vouloir nous raconter toi aussi tes
                    aventures et ressentis, n'hésites pas à en créer un!
                </p>
                <a
                    use:link
                    href="/register"
                    aria-label="Aller vers la page de création de compte"
                    >&#x27BD; Par ici!</a
                >
            </div>
        </section>
    {/if}
</div>
