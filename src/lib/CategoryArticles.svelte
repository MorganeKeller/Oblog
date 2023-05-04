<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/categoryArticles.scss";

  import { onMount } from "svelte";

  let articles = [];
  var tabAuthor = [];
  export let params = {};

  const getArticlesByContinent = async () => {
    const endpoint =
      import.meta.env.VITE_URL_DIRECTUS +
      `items/article?fields=*&filter[category_id][_eq]=${params.categoryId}&sort=-created_at`;
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

  onMount(() => {
    getArticlesByContinent();
  });

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

<section class="category-articles">
  <h1>Liste des articles</h1>
  {#each articles as article}

    <article class="each_articleList">
      <h2>{article.title}</h2>

      <div class="phototext">
        <a use:link href="/article/{article.id}"
          >
        <img class="taille" src={article.pictures} alt="illustration" /></a>
        <p class="overflow-ellipsis">{article.content}</p>
      </div>

        <a use:link href="/article/{article.id}">Lire la suite</a>

        <div class="infos">
        <p><strong>{tabAuthor[article.author]}</strong></p>
        <time datetime={article.created_at}
          >{new Date(article.created_at).toLocaleDateString("fr-FR")}</time
        >
        </div>
      
    </article>

  {/each}
</section>
