<script>
    import LogoMail from "../assets/img/mail.png" ;
    import LogoTwitter from "../assets/img/twitter.png";
    import LogoInsta from "../assets/img/instagram.png";
    import LogoFile from "../assets/img/google-docs.png";
    import LogoCita from "../assets/img/citation.png"
    import LogoPen from "../assets/img/signature.png";

    import { link } from "svelte-spa-router";
</script>

<footer>
    <ul id="footer-bloc">
        <div class="foot-elem">
            <li>nous contacter</li>
            <a
                use:link
                href="/contact"
                aria-label="redirection vers formulaire de contact"
                ><img src={LogoMail} alt="Logo Contact" /></a
            >
        </div>
        <div class="foot-elem">
            <li>nous suivre</li>
            <div class="foot-rs">
                <a
                    use:link
                    href="/error"
                    aria-label="Redirection vers notre page Twitter"
                    ><img src={LogoTwitter} alt="Logo Twitter" /></a
                >
               
                <a
                    use:link
                    href="/error"
                    aria-label="Redirection vers notre page Instagram"
                    ><img src={LogoInsta} alt="Logo Instagram" /></a
                >
            </div>
        </div>
        <div class="foot-elem">
            <li>CGU</li>
            <a
                use:link
                href="/cgu"
                aria-label="Redirection vers les Conditions générales d'utilisation"
                ><img src={LogoFile} alt="Logo documents" /></a
            >
        </div>
        <div class="foot-elem">
            <li>citations</li>
            <a
                use:link
                href="/quotes"
                aria-label="Redirection vers la page de citations"
                ><img src={LogoCita} alt="Logo bulle de discussion" /></a
            >
        </div>

        <div class="foot-elem">
            <li>votre article</li>
            <a
                use:link
                href="/createArticle"
                aria-label="Redirection vers la création d'un article"
                ><img src={LogoPen} alt="Logo de stylo" /></a
            >
        </div>
    </ul>
</footer>
<style>
    
</style>