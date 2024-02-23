<script>
    export let srcImg;
    export let srcImgHover;
    export let title;
    export let description;
</script>

<a href="#">
    <div class="project">
        <h2>
            {title}
        </h2>
        <p>{description}</p>
        <div class="gradiant"></div>
        <img src="{srcImg}" alt="{title}">
        <img class="imgHover" src="{srcImgHover}" alt="{title}">

        <p class="link">En savoir plus</p>
    </div>
    <p class="link mobileLink">En savoir plus</p>
</a>





<style lang="scss">

    .link{
        position: absolute;
        top: 85%;
        right: 70%;
        text-decoration: underline;
    }

h2, p{
    z-index: 90000;
    margin: 0;
    opacity: 0;
    transition: 0.5s ease;
}

a:hover{
    text-decoration: none;
}

    .project{
        width: 479px;
        height: 305px;
        overflow: hidden;
        border-radius: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        position: relative;
        transition: 0.5s ease;

        &:hover{
            transform: scale(105%);
            z-index: 10000;
            .imgHover{
                opacity: 1;
            }
            .gradiant{
                opacity: 0.8;
            }
            h2, p{
                opacity: 1;
            }
            @media screen and (max-width: 834px) {
                .link{
                    opacity: 0;
                }
            }
            
        }
    }
    img{
        position: absolute;
        object-fit: fill;
        width: inherit;
        height: fit-content;
        transition: 1s ease;
    }

    .imgHover{
        opacity: 0;
    }

    .gradiant{
        opacity: 0;
        z-index: 1000;
        width: 100%;
        height: 100%;
        position: absolute;
        background: rgb(114,19,148);
        background: linear-gradient(180deg, rgba(114,19,148,1) 0%, rgba(156,82,139,1) 100%);
        transition: 1s ease;
    }

    .mobileLink{

        position: absolute;
        bottom: 0;
        left: 0;
        transform: translate(0%, 150%);
        opacity: 0;

    }

    a{
        position: relative;
        width: fit-content;
        height: fit-content;
    }

    @media screen and (max-width: 834px) {
        .link{
            opacity: 0;
        }
        .mobileLink{
            opacity: 1;
        }

    }

@media screen and (max-width: 616px) {
        a{
            transform: scale(50%);
        }

}
</style>

