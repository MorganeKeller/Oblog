<script>
    import { link } from "svelte-spa-router";

    import "../assets/scss/error.scss";
</script>

<section id="section-404">
    <div class="bloc-error">
        <h1>Oups!</h1>
        <p>
            Il semblerait que tu te sois perdu ou que la page recherchée n'ait
            pas été trouvée...
        </p>
        <p>
            Pour retourner à l'accueil c'est <a
                use:link
                href="/home"
                aria-label="retour vers l'accueil">par ici</a
            >
        </p>
    </div>
</section>
