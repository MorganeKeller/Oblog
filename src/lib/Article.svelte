<script>
    import akihabara from "../assets/img/Akihabara.jpg";
    import chateau from "../assets/img/chateau_oasaka.jpg";
    import mont_fuji from "../assets/img/Mont_Fuji.jpg";

    
</script>

<article>
    <h1>Le Japon</h1>

    <div class="img-back" />

    <h2>Le quartier geek d'Akihabara</h2>

    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis similique minus id maxime, quo, nihil aut praesentium aliquid nam ad dolorem earum dignissimos sed. Ut, tenetur ipsam deserunt minima eaque fugiat quisquam laudantium quod doloremque! Repellendus debitis perspiciatis dolore sit illum magni ad minus unde qui cumque amet tempore inventore beatae eaque aut, dicta placeat perferendis enim mollitia. Molestias, iure!
    </p>

    <img src={akihabara} alt="quartier geek" aria-label="photo d'akihabara" />

    <h2>Le magnifique château d'Osaka</h2>

    <!-- ici il serait intéressant de pouvoir agrandir l'image lorsqu'on clique dessus -->
    <img class="little-img" src={mont_fuji} alt="photo du mont fuji" />

    <p class="p-right">
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Unde impedit,
        eos ipsam officiis repellat aperiam debitis necessitatibus ad fugit
        laborum quas, maxime reiciendis temporibus provident, inventore atque
        architecto! Nemo, quidem.
    </p>

    <p>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eos, atque
        amet odit corporis commodi ut.
    </p>
    <img src={chateau} alt="chateau d'osaka" />

    <p>Votre commentaire :</p>
    <textarea name="Commentaires" id="Votre commentaire" cols="40" rows="10" />
</article>

<style>
</style>