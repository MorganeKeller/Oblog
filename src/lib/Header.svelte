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
        <a href="" title="Carnets de voyages" aria-label="accueil du site">
            <img class="logo" src={logo} alt="Logo du site" />
        </a>

        <div>
            <input type="search" name="" placeholder="rechercher..." />
            <button aria-label="Bouton pour lancer la recherche">Go!</button>
        </div>
        <div id="mySidenav" class="sidenav">
            <ul role="menu" aria-labelledby="menubutton">
                <li role="presentation">
                    <a role="menuitem" href="/Home.svelte">Accueil</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Articles</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Destinations</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Auteurs</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Connexion</a>
                </li>
            </ul>
        </div>
    </nav>
</header>
