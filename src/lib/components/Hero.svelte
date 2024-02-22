<script></script>

<section>

    <h1>
        PORTFOLIO
    </h1>

    <h2>
        Hugo MENSAH
    </h2>

    <div class="scroll">
        <img class="textScroll" src="/scroll.svg" alt="Défilez en bas">
        <img class="arrow" src="/arrow.svg" alt="Défilez en bas"/>
    </div>
</section>
<style>
    section{
        /* position: absolute; */
        /* top: 0; */
        padding-top: 20vh;
        /* height: 190vh; */
        height: 100vh; 
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 2rem;
        position: relative;
        overflow-x: hidden;
        width: 100vw;
        /* padding-bottom: 71rem;  */
    }

    .scroll{
        margin-top: 168px;
        position: relative;
        width: 116px;
        height: 114px;
    }

    .scroll img{
        position: absolute;

    }

    .textScroll{
        animation: Rotate linear infinite  20s;
    }

    .arrow{
        left: 50%;
        transform: translate(-50%, 100%);
        animation: upDown linear infinite  5s;
    }


    @keyframes upDown{
        0%{
            transform: translate(-50%, 100%);
        }

        50%{
            transform: translate(-50%, 80%);
        }

        100%{
            transform: translate(-50%, 100%);
        }
    }

    @keyframes Rotate{
        0%{
            transform: rotate(0deg);
        }
        100%{
            transform: rotate(-360deg);
        }
    }


    
</style>