<script>
    export let title;
    
</script>



<section>
    <h2>{title}</h2>

    <div class="scroll">
        <slot></slot>
    </div>
</section>


<style lang="scss">
    section{
        display: flex;
        justify-content: flex-start;
        gap: 1rem;
        align-items: center;
    }
    h2{
        width: 442px;
        text-align: center;
        margin: 0;
    }

    .scroll{
        height: auto;
        width: -webkit-fill-available;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        gap: 50px;
        overflow-x: scroll;
        position: relative;
    }

    @media screen and (max-width: 970px) {
            section{
                align-items: start;
                flex-direction: column;
                h2{
                    width: fit-content;
                }
                
            }
    }
</style>