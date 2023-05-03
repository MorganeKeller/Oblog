<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/categoryArticles.scss";

  export let categoryId;

  let articles = [];

  const getArticlesByCategory = async () => {
    try {
      const response = await fetch(`${import.meta.env.VITE_URL_DIRECTUS}/items/article?fields=*&filter[category_id][_eq]=${categoryId}&sort=-created_at`);
      if (response.ok) {
        const json = await response.json();
        articles = json.data;
      } else {
        console.error('Server returned ' + response.status + ' ' + response.statusText);
      }
    } catch (e) {
      console.error('An error occurred while fetching articles', e);
    }
  };

  getArticlesByCategory();
</script>

<section class="category-articles">
  <h1>Articles de la catégorie</h1>

  <div class="articles-grid">
    {#if articles.length > 0}
      {#each articles as article}
        <div class="article-card" use:link={`/article/${article.id}`}>
          <h2>{article.title}</h2>
          <div class="author-date">
            <p>
              Par: <b>{article.author}</b>
              Le: <b><time datetime={article.created_at}>{new Date(article.created_at).toLocaleDateString('fr-FR')}</time></b>
            </p>
          </div>
        </div>
      {/each}
    {:else}
      <p>Aucun article trouvé.</p>
    {/if}
  </div>
</section>
