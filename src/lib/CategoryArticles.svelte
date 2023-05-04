<script>
  import { link } from "svelte-spa-router";
  import "../assets/scss/articleList.scss";

  export let params = {};

  let category_id = params.category_id;
  let articles = [];

  const getArticlesByCategory = async (category_id) => {
    try {
      const endpoint =
        import.meta.env.VITE_URL_DIRECTUS +
        `items/article?fields=*&filter[category_id][_eq]=${category_id}&sort=created_at`;
      const response = await fetch(endpoint);

      if (!response.ok) {
        throw new Error(`API request failed: ${response.status}`);
      }

      const json = await response.json();

      if (json.data) {
        articles = json.data.map((article) => {
          return {
            ...article,
            pictures:
              "http://chara-redif.vpnuser.lan/directus/uploads/" +
              article.pictures +
              ".jpg",
          };
        });
      } else {
        console.error("Invalid API response:", json);
      }
    } catch (error) {
      console.error("Error fetching articles:", error);
    }
  };

  // Utilisez la fonction reactive de Svelte pour mettre à jour les articles lors de la modification de category_id
  $: category_id && getArticlesByCategory(category_id);
</script>

<section class="articles">
  <h1>Articles par catégorie</h1>
  <div class="articles-list">
    {#each articles as article}
      <div class="article-card" use:link={`/article/${article.id}`}>
        <h2>{article.title}</h2>
        <img src={article.pictures} alt={article.title} />
        <div class="author-date">
          <p>
            Par: <b>{article.author}</b>
            Le:
            <b
              ><time datetime={article.created_at}
                >{new Date(article.created_at).toLocaleDateString(
                  "fr-FR"
                )}</time
              ></b
            >
          </p>
        </div>
      </div>
    {/each}
  </div>
</section>
