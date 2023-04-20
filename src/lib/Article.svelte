<script>
    import akihabara from "../assets/img/Akihabara.jpg";
    import chateau from "../assets/img/chateau_oasaka.jpg";
    import mont_fuji from "../assets/img/Mont_Fuji.jpg";

    import article from "../assets/scss/article.scss";

    import Comments from "./Comments.svelte";
    // export let params = {};
    // let article_id = params.id;
</script>

<article class="art">
    <h1>Le Japon</h1>

    

    <h2>Le quartier geek d'Akihabara</h2>

    <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dolores dicta
        nulla esse voluptatibus, vel voluptatum sit. Consectetur, voluptate
        voluptatum maiores nulla harum distinctio dolorum incidunt quibusdam ut
        minima possimus velit sapiente, iure hic. Inventore voluptates quos odio
        corporis optio. Provident aperiam nam porro dolore perspiciatis
        recusandae dolores numquam fugit quia in voluptate ipsum neque eveniet
        sint minus, vero expedita corporis.
    </p>

    <img src={chateau} alt="" />

    <Comments />
</article>

<style>
</style>
