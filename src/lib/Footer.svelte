<script>
    import LogoMail from "../assets/img/mail(1).svg";
    import LogoTwitter from "../assets/img/twitter(1).svg";
    import LogoTiktok from "../assets/img/tiktok.svg";
    import LogoInsta from "../assets/img/instagram(1).svg";
    import LogoFile from "../assets/img/file-text(1).svg";
    import LogoUser from "../assets/img/user(1).svg";
    import LogoPen from "../assets/img/pen-tool.svg";

    import { link } from "svelte-spa-router";

</script>

<footer>
    <ul>
        <div class="foot-elem">
            <li>nous contacter</li>
            <a use:link href="/contact" aria-label="redirection vers formulaire de contact"
                ><img src={LogoMail} alt="Logo Contact" /></a
            >
        </div>
        <div class="foot-elem">
            <li>nous suivre</li>
            <div class="foot-rs">
                <a use:link href="/error" aria-label="Redirection vers notre page Twitter"
                    ><img src={LogoTwitter} alt="Logo Twitter" /></a
                >
                <a use:link href="/error" aria-label="Redirection vers notre page Tiktok"
                    ><img src={LogoTiktok} alt="Logo Tiktok" /></a
                >
                <a use:link href="/error" aria-label="Redirection vers notre page Instagram"
                    ><img src={LogoInsta} alt="Logo Instagram" /></a
                >
            </div>
        </div>
        <div class="foot-elem">
            <li>CGU</li>
            <a use:link
                href="/cgu"
                aria-label="Redirection vers les Conditions générales d'utilisation"
                ><img src={LogoFile} alt="Logo documents" /></a
            >
        </div>
        <div class="foot-elem">
            <li>votre article</li>
            <a use:link href="/createArticle"><img src={LogoPen} alt="Logo de stylo" /></a>
        </div>
    </ul>
</footer>
