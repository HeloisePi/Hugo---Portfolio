<script>
    export let title1;
    export let title2;
    export let link;
    export let linkTitle;
    export let description;
    export let tag1;
    export let tag1Color;
    export let tag2;
    export let tag2Color;
    export let tag3;
    export let tag3Color;
    export let tag4;
    export let tag4Color;

    console.log("link", link)
</script>

<div class="contenaire" id="{title1}">
    <div class="cadre cadre1"></div>
    <div class="cadre cadre2"></div>
    <div class="top">
        <h2>{title1}</h2>
        <div class="tags">
            {#if tag1}
            <div class="tag">
                <div class="color" style="background-color:{tag1Color}">
                </div>
                <p  style="color:{tag1Color}">{tag1}</p>
            </div>
            {/if}
            {#if tag2}
            <div class="tag">
                <div class="color color2" style="background-color:{tag2Color}">
                </div>
                <p style="color:{tag2Color}"> {tag2}</p>
            </div>
            {/if}
            {#if tag3}
            <div class="tag">
                <div class="color color3" style="background-color:{tag3Color}">
                </div>
                <p style="color:{tag3Color}" >{tag3}</p>
            </div>
            {/if}
            {#if tag4}
            <div class="tag">
                <div class="color color4" style="background-color:{tag4Color}">
                </div>
                <p style="color:{tag4Color}"> {tag4}</p>
            </div>
            {/if}
        </div>
    </div>
    <div class="contenaireProject">
        <div class="visuelElement">
            <div class="contenaireElement">
            <slot></slot>
        </div>
        </div>
        <div class="titleDescription">
            <h3>{title2}</h3>
            <p>{description}</p>
        </div>
    </div>
    {#if link}
    <a target="blank" class="link" href="{link}"><p style="font-size: 20px;">{linkTitle}</p></a>
    {/if}
    {#if link==undefined }
    <a class="NotProject"href="#">Lien vers le projet                        </a>
    {/if }

</div>


<style lang="scss">
    @import '../../styles/global.scss';

    .NotProject{
        opacity: 0;
        cursor: initial;
    }

    a{
        z-index: 10;
    }

    .visuelElement{
        position: relative;
        width: 100%;
        height: 400px;
        .contenaireElement{
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000000;
        }
    }

    @media screen and (max-width: 1410px) {
        .contenaire .contenaireProject{
            align-items: center;
            justify-items: center;
            grid-template-columns: 1fr;
            grid-template-rows: max-content 340px;
            gap: 1rem;
            h3{
                position: absolute;
                top: 10%;
                left: 50%;
                transform: translateX(-50%);
                
            }
            p{
                transform: translateY(-25%);
            }

            .cadre1{
                transform: translate(-93px, -4px);
            }

            .contenaire .contenaireProject .contenaireProject .link{
                transform: translateY(-2rem) !important;
            }
            
            
        }
        .contenaire .cadre{
                width: 125%;
                z-index: 0;
            }
    }

    @media screen and (max-width: 1060px) {
        .contenaire {
            width: 80% ;
            
            h2{
                transform: translate(-13%, -4px);
            }

            .contenaireProject  h3{
                position: absolute;
                top: 10%;
                left: 50%;
                transform: translateX(-50%);
                
            }

            .cadre1{
                transform: translate(-11%, -4px);
            }

            .cadre2{
                transform: translate(-8%, 3.5rem);
            }

            a{
                transform: translateY(-2rem);
                z-index: 10;
            }

            .link{
                font-size: 20px;
               }

            .tag{
                background-color: #1e092200;
                padding: 0;
                
                p{
                    display: none;
                }
                .color{
                    margin: 0;
                    
                }
            }
        }
    }
    @media screen and (max-width: 550px) {
        .contenaire{
            a{
                transform: translateY(-3rem);
            }
            h2{
                font-size: 20px;
                margin-top: 20px;
            }
            .contenaireProject .titleDescription h3{
                font-size: 20px;
                top: 6%;
                white-space: wrap;
            }
        }
        .contenaire .contenaireProject{
            grid-template-rows: max-content 600px;
        }
    }

    @media screen and (max-width: 360px) {

        .contenaire .contenaireProject{

        grid-template-rows: max-content 700px;
        }
        .contenaire .contenaireProject p{
                transform: translateY(-10%);
            }
    }
        .cadre{
            background-color: $lightViolet;
            opacity: 0.1;
            position: absolute;
            width: 115%;
            height: 93%;
            top: 0;
            left: 0;
            border: 4px solid white;
            border-radius: 20px;
            z-index: 0;
            z-index: 0;
        }

        .cadre1{
            transform: translate(-139px, -4px);
        }

        .cadre2{
            transform: translate(-4rem, 4rem);
        }

        .contenaire{
            position: relative;
            width: 80%;
            display: flex;
            flex-direction: column;
            gap: 90px;
            z-index: 200;
            z-index: 0;
        }

        .top{
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .tags{
            display: flex;
            gap: 20px;
        }

        h2{
            margin: 0;
            white-space: nowrap;
        }

        h3{
            margin-bottom: 54px;
            //margin-top: 110px;
            white-space: nowrap;
        }
        .contenaireProject{
            display: grid;
            grid-template-columns: 1fr 1fr;

            z-index: 0;
        }

       .tag{
            background-color: #E8E8E8;
            border-radius: 10px;
            padding: 0.5rem;
            display: flex;
            align-items: center;
            width: fit-content;
            height: 30px;

        .color{
            width: 15px;
            height: 15px;
            border-radius: 50%;
            background-color: var(--tag1Color);
            margin-right: 0.5rem;
        }
        .color2{
            background-color: var(--tag2Color);
        }

        .color3{
            background-color: var(--tag3Color);
        }

        .color4{
            background-color: var(--tag4Color);
        }
    }


</style>