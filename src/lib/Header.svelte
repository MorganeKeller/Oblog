<script lang="ts">
    import logo from "../assets/img/logo.png";

    
    import BurgerMenu from 'svelte-burger-menu';

</script>


<header >

<BurgerMenu backgroundColor='grey' menuColor="red" position=relatif width= 300px font-weight: 400; text-align: center;>
    
    <ul role="menu" aria-labelledby="menuburger">
        <li role="presentation">
            <a role="menuitem" href="#">Accueil</a>
        </li>
        <li role="presentation">
            <a role="menuitem" href="#">Articles</a>
        </li>
        <li role="presentation">
            <a role="menuitem" href="#">Destinations</a>
        </li>
        <li role="presentation">
            <a role="menuitem" href="#">Auteurs</a>
        </li>
        <li role="presentation">
            <a role="menuitem" href="#">Connexion</a>
        </li>
    </ul>
	
</BurgerMenu>

    <nav>

        
            <a class="logo" href="" title="Carnets de voyages" aria-label="accueil du site">
                <img class="logo" src={logo} alt="Logo du site" />
            </a>

            <div>
                <input type="search" name="" placeholder="rechercher..." />
                <button aria-label="Bouton pour lancer la recherche">Go!</button>
            </div>
        

        <div class="navBar">
            <div >
                <ul role="menu" aria-labelledby="menubutton">
                    <li role="presentation">
                        <a role="menuitem" href="#">Accueil</a>
                    </li>
                    <li role="presentation">
                        <a role="menuitem" href="#">Articles</a>
                    </li>
                    <li role="presentation">
                        <a role="menuitem" href="#">Destinations</a>
                    </li>
                    <li role="presentation">
                        <a role="menuitem" href="#">Auteurs</a>
                    </li>
                    <li role="presentation">
                        <a role="menuitem" href="#">Connexion</a>
                    </li>
                </ul>
            </div>
    </div>

    </nav>

</header>


<style>

h2 {
	  font-size: 18px;
	  font-weight: 300;
	  padding-top: 10px;
	  padding-left: 3em;
	  padding-right: 4em;
	  cursor: pointer;
	  position: relative;
	  width: 80px;
	  height: 40px;
	  text-align: center;
	  float: center;
	  display: block;
	}

	h2:hover {
	  background-color: black;
	}
	img {
	  float: right;
	}
    
  </style>