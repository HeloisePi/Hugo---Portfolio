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
</script>

<div class="contenaire">
<div class="top">
<h2>{title1}</h2>
{#if tag1}
<div class="tag">
    <div class="color" style="background-color:{tag1Color}">
    </div>
    <p>{tag1}</p>
</div>
{/if}
{#if tag2}
<div class="tag">
    <div class="color" style="background-color:{tag2Color}">
    </div>
    <p>{tag2}</p>
</div>
{/if}
{#if tag3}
<div class="tag">
    <div class="color" style="background-color:{tag3Color}">
    </div>
    <p>{tag3}</p>
</div>
{/if}
{#if tag4}
<div class="tag">
    <div class="color" style="background-color:{tag4Color}">
    </div>
    <p>{tag4}</p>
</div>
{/if}
</div>
<div class="contenaireProject">
    <div class="visuelElement">
        <slot></slot>
    </div>
    <div class="titleDescription">
        <h3>{title2}</h3>
        <p>{description}</p>
    </div>
</div>
<a href="{link}"><p>{linkTitle}</p></a>
</div>
<div class="cadre"></div>


<style lang="scss">
       .tag{
        background-color: #E8E8E8;
        border-radius: 15px;
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

        }

        .color3{

        }

        .color4{

        }
    }


</style>