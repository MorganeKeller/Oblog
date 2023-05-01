<script>
    import logo from "../assets/img/logo.png";
    import { link } from "svelte-spa-router";

    // export let user_name;
    // let isLoggedIn = false;


    // const Getname = window.localStorage.getItem("user_name");
    // if (user_name) {
    //     isLoggedIn = true;
    // }

    // const toto = [
    //     {
    //         label: "Accueil",
    //         url: "/",
    //     },
    //     {
    //         label: "Articles",
    //         url: "articlesList",
    //     },
    //     {
    //         label: "Destinations",
    //         url: "/destinations",
    //     },
    //     {
    //         label: "Auteurs",
    //         url: "/authors",
    //     },
    //     {
    //         label: "Connexion",
    //         url: "/login",
    //     },
    // ];
</script>

<header>
    <nav class="nav">
        <div class="logo-search">
            <div class="logo">
                <a
                    use:link
                    href="/home"
                    title="Carnets de voyages"
                    aria-label="accueil du site"
                >
                    <img src={logo} alt="Logo du site" />
                </a>
            </div>
            <!-- <div class="searchbar">
                <input type="search" name="" placeholder="rechercher..." />
                <button aria-label="Bouton pour lancer la recherche">Go!</button
                >
            </div> -->
            <div>
                <!-- <p bind:this={Getname}>
                </p> -->
            </div>
        </div>
      
        <!-- {#each toto as item}
            <a use:link href={item.url}>{item.label}</a>
        {/each} -->
        <div class="nav-links">
          
            <a use:link href="/home">Accueil</a>
            <a use:link href="/articlesList">Articles</a>
            <a use:link href="/destinations">Destinations</a>
            <a use:link href="/authors">Auteurs</a>
            <a use:link href="/login">Connexion</a>
          
        </div>
    </nav>
</header>

<style>
</style>
