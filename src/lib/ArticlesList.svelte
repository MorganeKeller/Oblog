<script>
import tokyo from '../assets/img/Tokyo.jpg'
import new_zealand2 from '../assets/img/new_zealand2.jpg'
import grand_canyon from '../assets/img/grand_canyon.jpg'
import { link } from "svelte-spa-router";
</script>

    <section class="aurore-boreale_background">

        <div class="white-background">

                <h1>Vos expériences</h1>
                    <p>C'est ici que nous partageons nos expériences</p>

                    <h2>Ecris nous tes aventures</h2>
                        <a href="">A ta plume</a>
                
                    <article >
                        <h2>Le Japon</h2>
                        <img src="{tokyo}" alt=""/>
                        <strong>OY</strong>
                        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Alias officiis totam, ab a sed labore voluptatem natus corporis commodi voluptates consequuntur aspernatur maiores asperiores explicabo unde. Quos eveniet maxime voluptates! Excepturi dignissimos similique fuga. Id praesentium iusto in debitis tenetur dolorem nesciunt maiores aliquid! Enim?</p>
                        <a use:link href="/article">Lire la suite</a>
                    </article>

                    <article >
                        <h2>La Nouvelle-Zélande</h2>
                        <img src="{new_zealand2}" alt=""/>
                        <strong>MK</strong>
                        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Necessitatibus, unde, ipsam explicabo dicta minima nesciunt fugiat quia rerum reiciendis ad similique maxime illum, labore quisquam accusantium repellat accusamus a impedit. Tenetur perferendis, vel porro quam nulla labore, deserunt, possimus at magni iure soluta sint adipisci.</p>
                        <a href="">Lire la suite</a>
                    </article>

                    <article >
                        <h2>Les Etats-Unis</h2>
                        <img src="{grand_canyon}" alt=""/>
                        <strong>QP</strong>
                        <time datetime="2011-11-18T14:54:39">18 Nov 11</time>
                        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium eius facilis odit accusamus illo animi unde inventore eaque rerum, earum sapiente facere possimus minima aliquid quidem. Ullam tempora corporis est optio voluptatem eligendi tenetur voluptate reprehenderit? Quas perspiciatis unde, ipsa laboriosam iusto placeat ullam autem nihil cupiditate magnam earum aut excepturi eum ducimus distinctio at consequatur reiciendis aliquam ut doloremque.</p>
                        <a href="">Lire la suite</a>
                    </article>
        </div>            

    </section>

