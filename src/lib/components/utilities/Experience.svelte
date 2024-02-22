<script>
    export let date;
    export let IntitulePost;
</script>

<div class="experience">
    <h3>{date}</h3>
    <div>
      <h3>{IntitulePost}</h3>
      <div class="description">
        <slot></slot>
      </div>
       
    </div>
    <div class="backgroundExperience"></div>
  </div>
    
  
  <style lang="scss">
    @import '../../styles/global.scss';
    
    .experience {
        position: relative;
        margin: 110px;
        margin-top: 0;
        margin-bottom: 0;
        display: grid;
        align-items: center;
        grid-template-columns: 70% 30%;
        border-top: 2px solid $offWhite;
        padding: 47px;
        padding-left: 0;
        padding-right: 0;
        
        &:hover{
            .backgroundExperience{
                opacity: 5%;
            }
        }
      div {
        display: flex;
        flex-direction: column;
        gap: 2rem;
      }
      .description{
        gap: 1rem;
      }
    }
    @media screen and (max-width: 1000px) {
        .experience{
          grid-template-columns: 1fr;
          margin: 0px;
        }
        }

        .backgroundExperience{
            transition: opacity 0.25s ease-in;
            position: absolute;
            background-color: #9C528B;
            border-radius: 20px ;
            opacity: 0%;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            filter: blur(10px);
        }
  </style>