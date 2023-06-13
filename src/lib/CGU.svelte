<script>
    import "../assets/scss/cgu.scss";

    function goBack() {
        window.history.back();
    }
</script>

<section id="cgu-background">
    <h1>Conditions Générales d'Utilisation</h1>
    <div class="cgu-bloc">
        <p>
            Hey, ami voyageur ! Bienvenue sur notre blog « Carnet de voyages ».
            Avant de plonger dans nos récits palpitants, voici quelques règles à
            suivre :
        </p>
        <ul>
            <li>
                <u>Objectif de notre blog:</u> Notre but est de vous faire découvrir
                de nouveaux endroits, de vous inspirer à voyager et de vous donner
                des informations utiles pour planifier vos propres escapades. Nous
                nous engageons à vous fournir du contenu de qualité et régulièrement alimenté. Veuillez noter que ce blog n'a aucune vocation à devenir professionnel.
            </li>
            <li>
                <u>Utilisation de notre blog:</u> Notre blog est gratuit et accessible
                à tous les voyageurs quel que soit leur âge. Nous ne tolérons cependant pas les comportements
                irrespectueux ou offensants, et nous nous réservons le droit de refuser
                l'accès à notre blog à toute personne qui ne respecte pas ces valeurs.
            </li>
            <li>
                <u>Responsabilité:</u> Nous faisons tout notre possible pour publier
                et vérifier que les informations soient précises, mais nous ne pouvons
                garantir à 100% l'exactitude de toutes les informations fournies.
                Nous déclinons toute responsabilité en cas d'erreur ou d'omission.
            </li>
            <li>
                <u>Propriété intellectuelle:</u> Veuillez accepter que les
                contenus publiés sur notre blog deviennent, dès leur
                publication, libres de droits. <br />Nous nous réservons le
                droit en qualité de modérateurs de supprimer les contenus jugés
                contraires aux bonnes moeurs et valeurs promues par l'équipe des
                "Carnets de Voyages":
                <ul class="listing">
                    <li>
                        Contraire à la protection des personnes ou portant
                        atteinte à l'intégrité ou la vie privée d'une personne
                        ou d'une entité.
                    </li>
                    <li>
                        Incitation à la violence, à la haine ou à la
                        discrimination.
                    </li>
                    <li>A caractère obscène, pédophile ou pornographique.</li>
                   
                </ul>
                Nous laissons à disposition de ceux qui le veulent, l'entière possibilité
                de réutiliser nos contenus. Toutefois, n'hésitez pas à nous citer
                si tel était le cas.
            </li>
            <li>
                <u>Commentaires:</u> Nous encourageons les commentaires et les échanges
                constructifs sur notre blog, mais nous nous réservons le droit de
                supprimer tout commentaire qui ne respecte pas notre politique de
                modération. Nous n'acceptons pas les commentaires injurieux, discriminatoires
                ou promotionnels.
            </li>
            <li>
                <u>Modifications:</u> Nous pouvons être amenés à modifier nos CGU
                à tout moment, sans préavis. Nous vous invitons à les consulter régulièrement
                pour vous tenir informé.
            </li>
            <li>
                <u>Conclusion:</u> Nous espérons que notre blog vous inspirera à
                voyager et à découvrir de nouveaux endroits. Si vous avez des questions
                ou des commentaires, n'hésitez pas à nous contacter. Nous vous souhaitons
                une bonne lecture et de belles découvertes !
            </li>
        </ul>
    </div>
    <p>
        Voilà, tu sais tout l’ami. Maintenant, en route vers de nouvelles
        aventures !
    </p>
    <button on:click={goBack}>Retour</button>
</section>
