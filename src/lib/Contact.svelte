<script>
  import "../assets/scss/contact.scss";

  function goBack() {
    window.history.back();
  }
</script>

<section>
  <div class="container">
    <h1>Formulaire de contact</h1>

    <p>
      Voici notre page de contact! Si tu aperçois une coquille, une erreur, un
      propos un peu déplacé avant qu'on ait pu mettre la main dessus, fais-le
      nous savoir ici. Ou alors, si tu veux juste nous envoyer un petit message
      pour nous dire ô combien on est chouette, ça marche aussi!
    </p>

    <form>
      <label>
        Votre nom :
        <input type="text" name="name" required />
      </label>

      <label>
        E-mail :
        <input type="email" name="email" required />
      </label>

      <label>
        Votre message :
        <textarea name="message" required />
      </label>

      <button type="submit">Envoyer</button>
    </form>

    
    <button on:click={goBack}>Retour</button>
  </div>
</section>
