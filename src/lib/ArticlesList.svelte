<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/articleList.scss";

  export let params = {};

  // Extrait l'id issue de la route
  let article_id = params.id;
  var tabAuthor = [];

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
          "https://oblogback-production.up.railway.app/assets/" +
          article.pictures,
      };
    });
  };

  getArticles();

  const getAuthors = async function () {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "users";

    const response = await fetch(endpoint);

    const json = await response.json();
    let authors1 = json.data;
    for (var index in authors1) {
      tabAuthor[authors1[index].id] = authors1[index].user_name;
    }
    return json.data;
  };
  getAuthors();
</script>

<section class="articleList-background">
  <h1>Tous nos articles</h1>

  <div class="content-center">
    <p>
      C'est ici que tu trouveras recensés tous nos articles!<br /> N'hésite pas toi
      aussi à nous raconter tes ressentis. (Pas d'inquiétude nous n'attendons pas
      de textes à rallonge ou de mémoire de fin d'études, on aime les petits articles
      faciles et agréables à parcourir.) Pour participer c'est:
    </p>

    <a use:link href="/createArticle"> &#x27BD; Par ici!</a>
  </div>
  <article class="each_articleList">
    {#each articles as article}
      <div class="one-article">
        <div class="phototext">
          <a use:link href="/article/{article.id}"
            ><img
              class="taille"
              src={article.pictures}
              alt="Illustration en rapport avec l'article concerné"
            /></a
          >
        </div>

        <h2>{article.title}</h2>
        <p class="overflow-ellipsis">{article.content}</p>
        <a use:link href="/article/{article.id}">Lire la suite...</a>

        <div class="infos">
          <p><strong>{tabAuthor[article.author]}</strong></p>
          <time datetime={article.created_at}>
            {new Date(article.created_at).toLocaleDateString("fr-FR")}
          </time>
        </div>
      </div>
    {/each}
  </article>
</section>
