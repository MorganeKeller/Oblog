<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/register.scss";

  // Fonction pour créer un nouvel utilisateur
  async function createUser(first_name, last_name, user_name, email, password) {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";
    const data = {
      first_name: first_name,
      last_name: last_name,
      pseudo: user_name,
      email: email,
      password: password,
      role: "f3bb8d0e-b035-4c9c-8ce7-928dd1171be9",
    };
    const response = await fetch(endpoint, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(data),
    });

    if (!response.ok) {
      throw new Error("Erreur lors de la création de l'utilisateur.");
    }

    const user = await response.json();
    return user;
  }

  async function handleSubmit(event) {
    event.preventDefault();
    const form = event.target;
    const { first_name, last_name, user_name, email, password } = form.elements;

    const user = await createUser(
      first_name.value,
      last_name.value,
      user_name.value,
      email.value,
      password.value
    );

    // Traiter la réponse de la création d'utilisateur
    if (user) {
      console.log("Utilisateur créé avec succès !");
      // Rediriger l'utilisateur vers la page de connexion
    } else {
      console.log("Erreur lors de la création de l'utilisateur.");
      // Afficher un message d'erreur à l'utilisateur
    }
  }
</script>

<section class="main-register">
  <h1>Création de compte</h1>
  <div class="before-register">
    <p>
      Avant de te créer un compte on souhaiterait que tu jettes un oeil à nos <a
        use:link
        href="/cgu" aria-label="Redirection vers les Conditions Générales d'Utilisation">&#x27BD; Conditions Générales</a
      >
    </p>
  </div>

  <form on:submit={handleSubmit} aria-label="Informations d'enregistrement">
    <div class="register-form">
      <label for="first_name">Nom</label>
      <input required name="first_name" placeholder="ex : NEWTON" />
      <label for="last_name">Prénom</label>
      <input required name="last_name" placeholder="ex : Isaac" />
      <label for="pseudo">Pseudo</label>
      <input required name="pseudo" placeholder="ex=Isaacnewton23" />

      <label for="email">Email</label>
      <input
        required
        type="email"
        name="email"
        placeholder="ex : i.newton@test.fr"
      />

      <label for="password">Mot de passe</label>
      <input required type="password" name="password" placeholder="********" />

      <button class="btn-primary" type="submit">Créer mon compte</button>
    </div>
  </form>
  <div class="footer-register">
    <p>
      Tu as déjà un compte ? Connecte-toi <a use:link href="/login">ici</a>
    </p>
  </div>
</section>
