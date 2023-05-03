<script>
  import { link } from "svelte-spa-router";
  import { onMount } from 'svelte';

  let articles = [];

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
</script>

<section class="category-articles">
  <h1>Articles de la catégorie</h1>
  {#each articles as article}
      <article class="each_articleList">
        <h3>{article.title}</h3>
        <div class="alignement">
          <img class="taille" src={article.pictures} alt="illustration" />
          <p><strong>{article.author}</strong></p>
          <time datetime={article.created_at}
            >{new Date(article.created_at).toLocaleDateString("fr-FR")}</time
          >
          <p>{article.content}</p>
          <a use:link href="/article/{article.id}">Lire la suite</a>
        </div>
      </article>
    {/each}
  
</section>
