<script>
    import { onMount } from 'svelte';
  
    let slideClosed = true;
  
    onMount(() => {
      const headermobile = document.querySelector(".headermobile");
      const toggleOpen = document.querySelector(".toggle-open");
      const toggleClose = document.querySelector(".toggle-close");
      const slide = document.querySelector(".slide");
      const links = document.querySelectorAll('.close-menu');
  
      toggleOpen.addEventListener("click", function () {
        slide.classList.toggle("close");
        toggleOpen.classList.toggle("is-close");
        slideClosed = !slideClosed;
      });
      
      toggleClose.addEventListener("click", function () {
        slide.classList.add("close");
        toggleOpen.classList.toggle("is-close");
        slideClosed = true;
      });
  
      links.forEach(link => {
        link.addEventListener('click', () => {
          slide.classList.add('close');
          toggleOpen.classList.toggle("is-close");
          slideClosed = true;
        });
      });
    });
</script>

<section>
  <div class="headermobile">
    <div class="headershow">
      <a href="/"><h4>Hugo MENSAH</h4></a>
      <div class="toggle toggle-open">
        <img class="menu-line" src="/icon/menu.svg" alt="menu">
      </div>
    </div>
    <div class="slide {slideClosed ? 'close' : ''}">
      <div class="toggle toggle-close">
        <img class="menu-line" src="/icon/cross.svg" alt="fermer le menu">
      </div>
      <a class="close-menu" href="/#experience"><h3>Expériences</h3></a>
      <a class="close-menu" href="/projets"><h3>Projets</h3></a>
      <a class="close-menu" href="/dessin"><h3>Dessins</h3></a>
      <a class="close-menu" href="/#contact"><h3>Contacts</h3></a>
      <a class="close-menu" href="/#home"><h3>CV</h3></a>

      <img class="stain" src="/stain/stain1.svg" alt="">
    </div>
  </div>
</section>

<style lang="scss">
    @import '../../styles/global.scss';

    section {
      overflow: hidden;
      position: relative;
    }
  
    .headermobile {
      top: 0;
      left: 0;
      z-index: 3;
      position: fixed;
  
      .headershow {
        height: 65px;
        width: 100vw;
        display: flex;
        justify-content: center;
        align-items: center;
  
        .toggle {
          width: 25px;
          height: 25px;
          position: absolute;
          right: 20px;
          top: 20px;
          left: auto;
          z-index: 99999999999;
  
          .menu-line {
            width: 100%;
            height: 100%;

  
            &:before {
              content: '';
              height: 3px;
              width: 100%;
              position: absolute;
              -webkit-transform-origin: left;
              transform-origin: left;
              -webkit-transition: -webkit-transform .25s;
              -webkit-transition: all .25s;
              transition: all .25s;
              top: 10px;
              background-color: #ffffff;
            }
  
            &:after {
              content: '';
              height: 3px;
              width: 100%;
              position: absolute;
              -webkit-transform-origin: left;
              transform-origin: left;
              -webkit-transition: -webkit-transform .25s;
              -webkit-transition: all .25s;
              transition: all .25s;
              top: -10px;
              background-color: #ffffff;
            }
          }
        }
  
        img {
          width: 25px;
          height: 23px;
          margin-right: 20px;
        }
  
        .logo {
          width: 65px;
          height: 65px;
        }
      }
  
      
  
      .slide {
        background-color: $darkViolet;
        height: 100vh;
        width: 100vw;
        border-top-left-radius: 0%;
        border-top-right-radius: 0%;
        border-bottom-right-radius: 0%;
        border-bottom-left-radius: 0%;
        right: 0%;
        top: 0;
        position: absolute;
        padding: 5%;
        transition:  1s ease-in-out;
        display: flex;
        justify-content: center;
        align-items: center ;
        flex-direction: column;
        gap: 14px;
        z-index: 999999999999999999999999;
        //transition: border 3s ease-in-out;
        

        .stain{
            position: absolute;
            bottom: -40px;
            left: 50%;
            transform: translateX(-50%);
            filter: blur(432.32px);
        }
      }
      .close {
        transform: translateX(100%);
        border-top-left-radius: 50%;
        border-top-right-radius: 0%;
        border-bottom-right-radius: 0%;
        border-bottom-left-radius: 5%;
        
      }

      .toggle-close{
        img{
            position: absolute;
    top: 20px;
    right: 20px;
        }
      }
      
    }

</style>
