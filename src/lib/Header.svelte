<script>
    import logo from "../assets/img/logo.png";
    import { link } from "svelte-spa-router";

    const links = [
        {
            label: "Accueil",
            url: "/home",
        },
        {
            label: "Articles",
            url: "/articlesList",
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
        },
    ];
</script>

<header>
    <nav class="nav">
        
            <a
                use:link
                href="/home"
                title="Carnets de voyages"
                aria-label="lien vers la page d'accueil du site"
            >
                <img src={logo} alt="Logo du site" />
            </a>
       

        <div class="nav-links">
            {#each links as item}
                <a use:link href={item.url}>{item.label}</a>
            {/each}
        </div>
    </nav>
</header>

<style>
</style>
