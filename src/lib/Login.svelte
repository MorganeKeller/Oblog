<script>
    import { link } from "svelte-spa-router";
    import login from "../assets/scss/login.scss";

    import { push } from "svelte-spa-router";

    export let reload = false;
    let email;
    let password;
    let error= '';
    
    const handleSubmit = async (event) => {
        event.preventDefault();
        const token = await connect();

        //In case of good return we follow the following instructions
        if (token !== false) {
            // storage in "localstorage"
            window.localStorage.setItem("token", token);

            if (reload === false) {
                //Redirect to homepage
                push("/home");
            } else {
                //Page reloading
                location.reload();
            }
        }
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
            error= 'Adresse e-mail ou mot de passe incorrect';
            return false;
        }
        
        const json = await response.json();
        // Extraction errors handling

        // Token recovery only
        return json.data.access_token;
    };

    console.log(error);
</script>

<div class="login-background">
    <h1>Connexion</h1>
    <section aria-labelledby="loginForm" class="section-form">
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
                />
            </div>

            <input
                class="connexion"
                type="submit"
                value=" &#x27BD; Se connecter"
            />
        </form>
        <div class="text-login-register">
            <p>Pas encore de compte?</p>
            <p>
                Si l'envie te prend de vouloir nous raconter toi aussi tes
                aventures et ressentis, n'hésites pas à en créer un!
            </p>
            <a use:link href="/register">&#x27BD; Par ici!</a>
        </div>
    </section>
</div>
