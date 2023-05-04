<script>
  import plane from "../assets/img/plane.png";

  import { link } from "svelte-spa-router";
  import "../assets/scss/welcome.scss";
</script>

<section class="welcome-img">
  <div class="text-over">
    <h1>CARNETS DE VOYAGES</h1>
    <a use:link href="/home" aria-label="Entrer dans le site"
      >Entrer...<img src={plane} alt="logo d'avion" /></a
    >
  </div>
</section>
