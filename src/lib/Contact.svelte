<script>
  import "../assets/scss/contact.scss";

</script>

<section class="container">
  <h1>Formulaire de contact</h1>

  <p>
    Voici notre page de contact! Si tu aperçois une coquille, une erreur, un
    propos un peu déplacé avant qu'on ait pu mettre la main dessus, fais-le nous
    savoir ici. Ou alors, si tu veux juste nous envoyer un petit message pour
    nous dire ô combien on est chouettes, ça marche aussi!
  </p>

  <form>
    <label for="name"> Votre nom :</label>
    <input
      type="text"
      name="name"
      required
      aria-label="Veuillez entrer votre nom"
    />

    <label for="email"> E-mail :</label>
    <input
      type="email"
      name="email"
      required
      aria-label="Renseignez votre e-mail"
    />

    <label for="text"> Votre message : </label>
    <textarea name="message" required aria-label="Rédigez ici votre texte" />

    <input class ="form-send" type="submit" aria-label="valider le formulaire" value="Envoyer" />
  </form>

</section>
