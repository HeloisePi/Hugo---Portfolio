<script>
    export let href;
</script>



<a href="{href}" style="width: fit-content;"><slot></slot></a>


<style lang="scss">
    @import '../../styles/global.scss';

    a{
        padding: 0.5rem;
        border-radius: 10px;
        border: 2px solid $offWhite;
        z-index: 2;
        text-decoration: underline;
        text-align: center;
        &:hover{
            text-decoration: underline;
            background-color: $lightViolet;
        }
        p{
            text-decoration: underline;
            color: $offWhite !important;
        }

    }
</style>