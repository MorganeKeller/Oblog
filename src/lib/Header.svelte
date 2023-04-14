<script>
    import logo from "../assets/img/logo.png";
    import { Hamburger } from "svelte-hamburgers";

    let open;
</script>

<header>
    <nav>
        <div class="logo">
            <a href="" title="Carnets de voyages" aria-label="accueil du site">
                <img src={logo} alt="Logo du site" />
            </a>
        </div>
        <div class="searchbar">
            <input type="search" name="" placeholder="rechercher..." />
            <button aria-label="Bouton pour lancer la recherche">Go!</button>
        </div>
        <div class="burger">
            <Hamburger bind:open />
            {#if open}
                <!-- show menu -->
                <a href=""><h2>Accueil</h2></a>
                <a href=""><h2>Articles</h2></a>
                <a href=""><h2>Destinations</h2></a>
                <a href=""><h2>Auteurs</h2></a>
                <a href=""><h2>Connexion</h2></a>
            {/if}
        </div>
    </nav>
</header>

<style>
</style>
