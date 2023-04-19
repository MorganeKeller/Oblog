<script>
    const init = async () => {
        const spaces = await getSpaces();
        console.log("spaces", spaces)

        const token = await login();
        console.log("token", token);

        const comments = await getComments(token);
        console.log("comments", comments);
    }


    // Fonction async en arriere
    // Elle prend 1sec a s'exécuter
    // Son seul but est de lire la liste des espaces sur directus et de les retourner
    const getSpaces = async () => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/space";
        const response = await fetch(endpoint);

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction

        return json.data;
    }


    const login = async () => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "auth/login";
        const response = await fetch(endpoint, {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify({
                email: "test@test.fr",
                password: "1234"
            })
        });

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction

        return json.data.access_token;
    }


    const getComments = async (token) => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/comments";
        const response = await fetch(endpoint, {
            headers: {
                "Authorization": "Bearer " + token
            }
        });

        // Gestion des erreurs de réponse

        const json = await response.json();

        // Gestion des erreurs d'extraction

        return json.data;
    }


    init();
</script>