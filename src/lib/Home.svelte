<script>
    import mont_fuji from '../assets/img/Mont_Fuji.jpg'
    import new_zealand from '../assets/img/new_zealand.jpg'
    import grand_canyon from '../assets/img/grand_canyon.jpg'
    import { link } from "svelte-spa-router";

    import home from '../assets/scss/home.scss';

</script>


<section class="home-background">


<h1>Bienvenue dans nos Carnets de Voyages!</h1>
<p class="text-center">
    Vous voici arrivés à destination: ici découvrez les derniers articles
    publiés
</p>
<div>
    <article >

        <h2>Le Japon</h2>
        
        <div >

        <img src={mont_fuji} alt="Mont Fuji">

        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Incidunt saepe iste quasi quas fuga libero culpa voluptate doloremque, officia doloribus facilis ipsa ad odit ducimus, quaerat delectus deserunt aperiam commodi.</p>

        <a use:link href="/article">Lire la suite</a>

        <p><strong>OY</strong></p>
        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>

    </article>

    <article >

        <h2>La nouvelle Zélande</h2>
        
        <div >

        <img src={new_zealand} alt="paysage de Nouvelle-Zélande">

        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Incidunt saepe iste quasi quas fuga libero culpa voluptate doloremque, officia doloribus facilis ipsa ad odit ducimus, quaerat delectus deserunt aperiam commodi.</p>

        <a use:link href="/article">Lire la suite</a>

        <p><strong>MK</strong></p>
        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>

    </article>

    <article >

        <h2>Les Etats-Unis</h2>
        
        <div >

        <img src={grand_canyon} alt="vue sur le Grand Canyon">

        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Incidunt saepe iste quasi quas fuga libero culpa voluptate doloremque, officia doloribus facilis ipsa ad odit ducimus, quaerat delectus deserunt aperiam commodi.</p>

        <a use:link href="/article">Lire la suite</a>

        <p><strong>QP</strong></p>
        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>

    </article>

</div>

</section>
