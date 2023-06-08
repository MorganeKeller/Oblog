<script>
  import { link } from "svelte-spa-router";
  import { onMount } from "svelte";

  import "../assets/scss/register.scss";
  // Initializing the message and the form visibility states
  let message = "";
  let formVisible = true;
  // Function to create a new user
  async function createUser(first_name, last_name, pseudo, email, password) {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";
    const data = {
      first_name: first_name,
      last_name: last_name,
      user_name: pseudo,
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
  // Function to handle form submission
  async function handleSubmit(event) {
    event.preventDefault();
    const form = event.target;
    const { first_name, last_name, pseudo, email, password } = form.elements;

    try {
      // Creating a new user
      const user = await createUser(
        first_name.value,
        last_name.value,
        pseudo.value,
        email.value,
        password.value
      );
      // Handling the user creation response
      // Traiter la réponse de la création d'utilisateur
      if (user) {
        message = "Votre compte a été créé avec succès !";
        formVisible = false;
      } else {
        message = "Erreur lors de la création de l'utilisateur.";
      }
    } catch (error) {
      console.log("Erreur lors de la création de l'utilisateur.", error);
      message = "Erreur lors de la création de l'utilisateur.";
    }
  }
  // Function to go back to previous page
  function goBack() {
    window.history.back();
  }
  // Attaching the form submission handler to the form
  onMount(() => {
    const form = document.getElementById("register-form");
    form.addEventListener("submit", handleSubmit);
  });
</script>

<section class="main-register">
  {#if formVisible}
    <div>
      <h1>Création de compte</h1>
      <div class="before-register">
        <p>
          Avant de te créer un compte on souhaiterait que tu jettes un oeil à
          nos
          <a use:link href="/cgu">&#x27BD; Conditions Générales</a>
        </p>
      </div>
      <form
        id="register-form"
        aria-label="Informations d'enregistrement"
        on:submit={handleSubmit}
      >
        <div class="register-form">
          <label for="last_name">Prénom</label>
          <input required name="first_name" placeholder="ex : NEWTON" />

          <label for="first_name">Nom</label>
          <input required name="last_name" placeholder="ex : Isaac" />

          <label for="email">Email</label>
          <input
            required
            type="email"
            name="email"
            placeholder="ex : i.newton@test.fr"
          />

          <label for="pseudonym">Pseudo</label>
          <input required name="pseudo" placeholder="ex=Isaacnewton23" />

          <label for="password">Mot de passe</label>
          <input
            required
            type="password"
            name="password"
            placeholder="********"
          />

          <button class="btn-creation" type="submit">Créer mon compte</button>
        </div>
      </form>
      <div class="footer-register">
        <p>
          Tu as déjà un compte ? Connecte-toi <a use:link href="/login"
            >&#x27BD; ici</a
          >
        </p>
      </div>
    </div>
  {:else}
    <div class="confirmation">
      <h2>Confirmation de création de compte</h2>
      <p>{message}</p>
    </div>
  {/if}
</section>
