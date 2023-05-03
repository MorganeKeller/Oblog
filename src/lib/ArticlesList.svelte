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
        "items/article?fields=*&sort=created_at";
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
  
  <section class="aurore-boreale_background">

    <div class="content-center">

      <h1>Nos expériences</h1>
  
      <p>
        C'est ici que nous partageons nos expériences. Raconte-nous aussi tes
        aventures!
      </p>
  
      <a use:link href="/createArticle"> A ta plume!</a>
  
      {#each articles as article}

        <article class="each_articleList">

          <h2>{article.title}</h2>

          <div class="alignement">
            <img class="taille" src={article.pictures} alt="illustration" />
            <p><strong>{article.author}</strong></p>
            <time datetime={article.created_at}
              >{new Date(article.created_at).toLocaleDateString("fr-FR")}</time
            >
            <p class="overflow-ellipsis">{article.content}</p>
        

            <a use:link href="/article/{article.id}">Lire la suite</a>
          </div>

        </article>

      {/each}
    </div>

  </section>
