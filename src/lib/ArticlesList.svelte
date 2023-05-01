<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/articleList.scss";

  export let params = {};

  // Extrait l'id issue de la route
  let article_id = params.id;

  let articles = [];

  const getArticles = async () => {
    const endpoint =
      import.meta.env.VITE_URL_DIRECTUS +
      "items/article?fields=*&sort=-created_at";
    const response = await fetch(endpoint);
    const json = await response.json();
    articles = json.data.map((article) => {
      return {
        ...article,
        pictures:
          "http://chara-redif.vpnuser.lan/directus/uploads/" +
          article.pictures +
          ".jpg",
      };
    });
  };

  getArticles();
</script>

<section class="articleList-background">
  <h1>Nos expériences</h1>

  <div class="content-center">
    <p>
      C'est ici que nous partageons nos expériences. N'hésite pas toi aussi à
      nous raconter tes aventures!
    </p>

    <a use:link href="/createArticle"> &#x27BD; A ta plume!</a>
  </div>

  {#each articles as article}
    <article class="each_articleList">
      
      <h2>{article.title}</h2>

      <div class="phototext">
        <img
          class="taille"
          src={article.pictures}
          alt="Illustration en rapport avec l'article concerné"
        />
        <p class="overflow-ellipsis">{article.content}</p>
      </div>

      <div class="infos">
        <b>{article.author}</b>
        <time datetime={article.created_at}>
          {new Date(article.created_at).toLocaleDateString("fr-FR")}
        </time>
      </div>

      <a use:link href="/article/{article.id}">Lire la suite...</a>
    </article>
  {/each}
</section>
