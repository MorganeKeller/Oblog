<script>
  import plane from "../assets/img/avion.png";

  import { link } from "svelte-spa-router";
  import "../assets/scss/welcome.scss";

  import { fade } from "svelte/transition";
  let visible = true;
</script>

<section class="welcome-img">
  <div class="text-over">
    <h1>CARNETS DE VOYAGES</h1>
    {#if visible}
      <a
        bind={visible}
        transition:fade={{ duration: 1500 }}
        use:link
        href="/home"
        aria-label="Entrer dans le site"
        >Entrer...<img src={plane} alt="logo d'avion" /></a
      >
    {/if}
  </div>
</section>
