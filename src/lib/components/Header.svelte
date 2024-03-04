<script>
  import { onMount } from 'svelte';

  let lastScrollTop = 0;
  let headerVisible = true;

  onMount(() => {
    window.addEventListener("scroll", handleScroll);
  });

  function handleScroll(event) {
    const currentScrollTop = window.pageYOffset || document.documentElement.scrollTop;
    
    if (currentScrollTop > lastScrollTop) {
      // Scroll vers le bas
      headerVisible = false;
    } else {
      // Scroll vers le haut
      headerVisible = true;
    }
    
    lastScrollTop = currentScrollTop <= 0 ? 0 : currentScrollTop;
  }
</script>

<header style="top: {headerVisible ? '0' : '-76px'}; {headerVisible ? 'background-color: $darkViolet;' : ''}">

  <a href="/" class="hugo"><h3>Hugo MENSAH</h3></a>

  <div class="links">
    <a href="../../#experience"><h3>Expériences</h3></a>
    <a href="/projets"><h3>Projets</h3></a>
    <a href="/dessin"><h3>Dessins</h3></a>
    <a href="../../#contact"><h3>Contacts</h3></a>
    <a target="blank" href="/CV-MENSAH-Hugo.pdf"><h3>CV</h3></a>
  </div>
</header>

<style lang="scss">
  @import '../styles/global.scss';
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 3rem;
    height: 76px;
    position: fixed;
    width: 100vw;
    z-index: 90000;
    transition: top 0.3s ease-in-out; /* Ajout de la transition */
  }

  .links {
    display: flex;
    justify-content: center;
    gap: 2rem;
    align-items: center;
    padding: 2rem;
    height: 76px;
  }

  .hugo {
    &:hover {
      color: $offWhite;
      text-decoration: none;
    }
  }
</style>