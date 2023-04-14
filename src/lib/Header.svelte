<script>
    import logo from "../assets/logo.png";

   
    import { link } from 'svelte-spa-router';
    import active from 'svelte-spa-router/active'    
   
    
    const navlinks = [
        {
            "label" : "Home",
            "url": "/" 
        },
        {
            "label" : "Contact",
            "url": "/contact" 
        },
        {
            "label" : "ArticlesList",
            "url": "/articleslist" 
        },
        {
            "label" : "Authors",
            "url": "/authors" 
        },
        {
            "label" : "CGU",
            "url": "/cgu" 
        },

    ];
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
                {#each navlinks as lien}
                <li role="presentation">
                    <a use:link role="menuitem" href="{lien.url}">{lien.label}</a>
                </li>
                {/each}
                <!-- <li role="presentation">
                    <a role="menuitem" href="/articleslist">Articles</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Destinations</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="/authors">Auteurs</a>
                </li>
                <li role="presentation">
                    <a role="menuitem" href="">Connexion</a> -->
                <!-- </li> -->
            </ul>
        </div>
    </nav>
</header>