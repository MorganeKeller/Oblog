<script>
  import logo from "../assets/img/logo.png";
  import plane from "../assets/img/plane.png";

  import { link } from "svelte-spa-router";

</script>

<section class="welcome-img">
  <div class="text-over">
    <h1>CARNETS DE VOYAGES</h1>
    <a use:link class="button" href="/home">Entrer...<img src={plane} alt="logo illustratif d'avion" /></a>
  </div>
</section>
