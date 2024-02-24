<script></script>

<section id="hero">

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
    #hero{
        /* position: absolute; */
        /* top: 0; */
        padding-top: 20vh;
        /* height: 190vh; */
        height: 100vh; 
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 1rem;
        position: relative;
        width: 100%;
        overflow: hidden;
    }

    @media screen and (max-height: 1000px) {
                #hero h1{
                    font-size: 48px;
                }
                h2{
                    font-size: 28px;
                }
                #hero .scroll{
                    width: 51px;
                    margin-top: 0px;
                    
                }
                #hero .arrow{
                    width: 10px;
                    height: auto;
                }

            }
            @media screen and (max-height: 500px) {
                #hero{
                    gap: 0;
                }
                h2{
                    margin-bottom: 40px;
                }
            }


    .scroll{
        margin-top: 5vh;
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