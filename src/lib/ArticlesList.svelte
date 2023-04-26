

   <script>
    import { link } from "svelte-spa-router";
    import articleList from "../assets/scss/articleList.scss";
  
    export let params = {};
  
    // Extrait l'id issue de la route
    let article_id = params.id;
  
    let articles = [];
  
    const getArticles = async () => {
      const endpoint = import.meta.env.VITE_URL_DIRECTUS + "items/article?fields=*&sort=created_at";
      const response = await fetch(endpoint);
      const json = await response.json();
      articles = json.data.map(article => {
        return {
          ...article,
          pictures: 'http://chara-redif.vpnuser.lan/directus/uploads/' + article.pictures + '.jpg'
        }
      });
    };
  
    getArticles();
  
    function goBack() {
      window.history.back();
    }
  </script>
  
  <section class="aurore-boreale_background">
    <div class="content-center">
      <h1>Vos expériences</h1>
      <h2>Ecris nous tes aventures</h2>
      <p>C'est ici que nous partageons nos expériences</p>
      <a use:link href=/createArticle>A ta plume</a>
  
      {#each articles as article}
      <article>
        <h3>{article.title}</h3>
        <div class="alignement">
          <img class="taille" src={article.pictures} alt="illustration">
          <p><strong>{article.author}</strong></p>
          <time datetime={article.created_at}>{new Date(article.created_at).toLocaleDateString('fr-FR')}</time>
          <p>{article.content}</p>
          <a use:link href="/article/{article.id}">Lire la suite</a>
        </div>
      </article>
      {/each}
  
      <button on:click={goBack}>Retour</button>
    </div>
  </section>
  