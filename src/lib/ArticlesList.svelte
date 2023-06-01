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
        <a use:link href="/article/{article.id}"
          ><img
            class="taille"
            src={article.pictures}
            alt="Illustration en rapport avec l'article concerné"
          /></a
        >
        <p class="overflow-ellipsis">{article.content}</p>
      </div>

      <a use:link href="/article/{article.id}">Lire la suite...</a>

      <div class="infos">
        <p><strong>{tabAuthor[article.author]}</strong></p>
        <time datetime={article.created_at}>
          {new Date(article.created_at).toLocaleDateString("fr-FR")}
        </time>
      </div>
    </article>
  {/each}
</section>
