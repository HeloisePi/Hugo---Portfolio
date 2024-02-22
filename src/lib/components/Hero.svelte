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

    <img class="stain stain1" src="/stain/stain1.svg" alt="tâche">
    <img class="stain stain2" src="/stain/stain2.svg" alt="tâche">
    <img class="stain stain3" src="/stain/stain3.svg" alt="tâche"> 

</section>
<style>
    section{
        position: absolute;
        top: 0;
        padding-top: 20vh;
        height: 190vh;
        /*height: 100vh; */
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 2rem;
        position: relative;
        overflow-x: hidden;
        width: 100vw;
        padding-bottom: 71rem; 
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


    .stain{
        position: absolute;
        z-index: 0;
        filter: blur(378.28px);
    }

    .stain1{
        left: 0;
        transform: translate(-50vw, 12vh);
        animation: RotateStain1 10s linear infinite; 
        width: 80%;

    }

    .stain2{
        right: 0;
        transform: translate(32rem, -52vh);
        animation: RotateStain2 15s linear infinite; 
        width: 50%;
    }

    .stain3{
        width: 72%;
        transform: translate(6vw, 1vh);
        width: 60%;
    }


    @keyframes RotateStain1{
        0%{
            transform: translate(-66vw, 3vh);
        }

        35%{
            transform: translate(-48vw, 36vh);
        }

        65%{
            transform: translate(-35vw, 0vh);
        }

        100%{
            transform:translate(-66vw, 3vh);
        }
    }

    @keyframes RotateStain2{
        0%{
            transform: translate(30vw, -30vh);
        }

        35%{
            transform: translate(30vw, 11vh);
        }

        65%{
            transform: translate(17vw, -16vh);
        }

        100%{
            transform: translate(30vw, -30vh);
        }
    }
</style>