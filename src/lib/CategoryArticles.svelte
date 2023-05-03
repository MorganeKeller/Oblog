<script>
  import { link } from "svelte-spa-router";
  import { onMount } from 'svelte';

  export let categoryId;

  const continents = ["Europe", "Asie", "Afrique", "Amérique du Nord", "Amérique du Sud", "Océanie"];
  let articlesByContinent = {};

  const getArticlesByContinent = async (continent) => {
    const endpoint =
      import.meta.env.VITE_URL_DIRECTUS +
      `items/article?fields=*&filter[category_id][_eq]=${categoryId}&filter[continent][_eq]=${continent}&sort=-created_at`;
    const response = await fetch(endpoint);
    const json = await response.json();
    articlesByContinent[continent] = json.data.map((article) => {
      return {
        ...article,
        pictures:
          import.meta.env.VITE_URL_DIRECTUS + "assets/" + article.pictures,
      };
    });
  };

  const getArticlesByCategory = async () => {
    for (let i = 0; i < continents.length; i++) {
      await getArticlesByContinent(continents[i]);
    }
  };

  onMount(() => {
    getArticlesByCategory();
  });
</script>

<section class="category-articles">
  <h1>Articles de la catégorie</h1>

  {#each continents as continent}
    <div class="articles-continent">
      <h2>{continent}</h2>
      {#if articlesByContinent[continent] && articlesByContinent[continent].length > 0}
        {#each articlesByContinent[continent] as article}
          <div class="article-card" use:link={`/article/${article.id}`}>
            <h3>{article.title}</h3>
            <img src={article.pictures} alt={article.title} />
            <div class="author-date">
              <p>
                Par: <b>{article.author}</b>
                Le: <b><time datetime={article.created_at}>{new Date(article.created_at).toLocaleDateString('fr-FR')}</time></b>
              </p>
            </div>
          </div>
        {/each}
      {:else}
        <p>Aucun article trouvé pour ce continent.</p>
      {/if}
    </div>
  {/each}
</section>
