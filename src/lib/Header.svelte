<script>

    import logo from "../assets/img/logo.png";

    import { link } from "svelte-spa-router";

    const links = [
        {
            label: "Accueil",
            url: "/",
        },
        {
            label: "Articles",
            url: "articlesList",
        },
        {
            label: "Destinations",
            url: "/destinations",
        },
        {
            label: "Auteurs",
            url: "/authors",
        },
        {
            label: "Connexion",
            url: "/login",
        },];
</script>
<header>
    <nav>

        <div class="logo">
            <a use:link href="/home" title="Carnets de voyages" aria-label="accueil du site">
                <img src={logo} alt="Logo du site" />
            </a>
        </div>
        <div class="searchbar">
            <input type="search" name="" placeholder="rechercher..." />
            <button aria-label="Bouton pour lancer la recherche">Go!</button>
        </div>
        
                <a use:link href="/home">Accueil</a>
                <a use:link href="/articles">Articles</a>
                <a use:link href="/destinations">Destinations</a>
                <a use:link href="/authors">Auteurs</a>
                <a use:link href="/login">Connexion</a>

    </nav>
</header>
